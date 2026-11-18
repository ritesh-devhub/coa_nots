COA – Chapter 4: Cache Memory
:::writing{variant="document" id="62841"}
# CHAPTER 4 – CACHE MEMORY
**Computer Organization and Architecture | William Stallings, 10th Edition**

---

## 1. Introduction to Computer Memory

Computer memory exhibits a wide range of types, technology, organization, performance and cost.

No single memory technology is optimal for satisfying all the memory requirements of a computer system.

Therefore, a typical computer system uses a **hierarchy of memory subsystems**.

Memory is broadly divided into:
1. Internal memory – Directly accessible by the processor.
2. External memory – Accessible by the processor through an I/O module.

The main purpose of memory hierarchy is to provide high speed, large capacity and reasonable cost.

---

## 2. Characteristics of Memory Systems

The most important characteristics of memory systems are:

### 2.1 Location

It refers to whether memory is internal or external to the computer.

**Internal Memory:**
- Often equated with main memory.
- Includes registers and cache memory.
- Directly accessible by the processor.

**External Memory:**
- Consists of peripheral storage devices.
- Examples: Hard disk and magnetic tape.
- Accessible to the processor through I/O controllers.

### 2.2 Capacity

Capacity refers to the amount of data that a memory can store.

- Memory capacity is typically expressed in bytes or words.
- 1 Byte = 8 Bits.
- Common word lengths are 8, 16 and 32 bits.

### 2.3 Unit of Transfer

It refers to the number of bits read out of or written into memory at a time.

For internal memory, it is equal to the number of electrical lines into and out of the memory module.

Three related concepts:

**A. Word**
- The natural unit of organization of memory.
- Its size is typically equal to the number of bits used to represent an integer and the instruction length.

**B. Addressable Units**
- It refers to the smallest unit of memory that can be individually addressed.
- Some systems use words as addressable units, while many systems allow addressing at the byte level.

Formula:

2^A = N

Where:
- A = Length of address in bits.
- N = Number of addressable units.

**C. Unit of Transfer**
- For main memory, it is the number of bits read out of or written into memory at a time.
- It need not be equal to a word or an addressable unit.
- For external memory, data is often transferred in larger units called blocks.

---

## 3. Methods of Accessing Units of Data

There are four methods of accessing memory:

### 3.1 Sequential Access

- Memory is organized into units of data called records.
- Access must be made in a specific linear sequence.
- A shared read-write mechanism is used.
- The mechanism must pass through intermediate records to reach the desired record.
- Access time is variable.

**Example:** Magnetic tape.

### 3.2 Direct Access

- Involves a shared read-write mechanism.
- Individual blocks or records have a unique address based on physical location.
- Access is made by reaching a general vicinity, followed by sequential searching or waiting to reach the final location.
- Access time is variable.

**Example:** Magnetic disk.

### 3.3 Random Access

- Each addressable location has a unique, physically wired-in addressing mechanism.
- Any location can be selected at random and directly accessed.
- Access time is independent of the sequence of prior accesses.
- Access time is constant.

**Examples:** Main memory and some cache systems.

### 3.4 Associative Access

- It is a type of random access memory.
- A word is retrieved based on a portion of its contents rather than its address.
- Desired bit locations are compared simultaneously for a specified match.
- Retrieval time is constant and independent of location or previous access patterns.

**Example:** Associative cache memory.

---

## 4. Capacity and Performance of Memory

The two most important characteristics of memory from a user's point of view are:

1. Capacity
2. Performance

Three performance parameters are used.

### 4.1 Access Time (Latency)

- It is the time taken to perform a read or write operation in random-access memory.
- For non-random-access memory, it is the time required to position the read-write mechanism at the desired location.

### 4.2 Memory Cycle Time

- It consists of access time plus any additional time required before a second access can commence.
- Additional time may be required for transients to die out on signal lines or to regenerate data if they are read destructively.
- It is concerned with the system bus, not the processor.

**Formula:**

Memory Cycle Time = Access Time + Additional Time

### 4.3 Transfer Rate

- It is the rate at which data can be transferred into or out of a memory unit.
- For random-access memory, it is equal to the reciprocal of cycle time.

**Formula:**

Transfer Rate = 1 / Memory Cycle Time

---

## 5. Physical Types and Characteristics of Memory

### Common physical types of memory

1. Semiconductor memory
2. Magnetic surface memory
3. Optical memory
4. Magneto-optical memory

### 5.1 Volatile Memory

- Information decays naturally or is lost when electrical power is switched off.
- Requires power to retain information.

**Example:** RAM.

### 5.2 Nonvolatile Memory

- Once recorded, information remains without deterioration until deliberately changed.
- No electrical power is needed to retain information.

**Example:** Magnetic-surface memory.

### 5.3 Nonerasable Memory

- Cannot be altered except by destroying the storage unit.
- Semiconductor memory of this type is known as Read-Only Memory (ROM).
- A practical nonerasable memory must also be nonvolatile.

### Memory Organization

For random-access memory, organization is a key design issue.

Organization refers to the physical arrangement of bits to form words.

---

## 6. Memory Hierarchy

Memory hierarchy is an arrangement of different memory types based on their speed, capacity and cost.

The design constraints of memory can be summarized by three questions:

1. How much?
2. How fast?
3. How expensive?

There is a trade-off among three important characteristics:

- Faster access time → Greater cost per bit.
- Greater capacity → Smaller cost per bit.
- Greater capacity → Slower access time.

### Why is Memory Hierarchy required?

A computer requires:
- Large memory capacity.
- High-speed memory.
- Low memory cost.

Using only one type of memory cannot satisfy all three requirements.

Therefore, smaller, more expensive and faster memories are supplemented by larger, cheaper and slower memories.

This arrangement is called **Memory Hierarchy**.

### Memory Hierarchy Arrangement

From fastest to slowest:

1. CPU Registers
2. Cache Memory
3. Main Memory (RAM)
4. Secondary Memory (SSD/HDD)
5. External Storage

### What happens as we move down the hierarchy?

1. Cost per bit decreases.
2. Capacity increases.
3. Access time increases.
4. Frequency of access by the processor decreases.

**Important:** Smaller, more expensive and faster memories are supplemented by larger, cheaper and slower memories.

### 6.1 Locality of Reference

Locality of reference is the principle that memory references by the processor, for both instructions and data, tend to cluster during program execution.

Programs typically contain iterative loops and subroutines.

Once a loop or subroutine is entered, there are repeated references to a small set of instructions.

Similarly, operations on tables and arrays involve access to a clustered set of data words.

Over a short period of time, the processor primarily works with fixed clusters of memory references.

**Types of Locality:**

1. Temporal Locality: If a particular memory location is accessed, it is likely to be accessed again in the near future.

   Example: Repeated execution of a loop.

2. Spatial Locality: If a particular memory location is accessed, nearby memory locations are likely to be accessed in the near future.

   Example: Accessing consecutive elements of an array.

### 6.2 Hit Ratio

Hit ratio is the fraction of all memory accesses that are found in the faster memory, such as cache.

**Formula:**

Hit Ratio (H) = Number of Cache Hits / Total Memory Accesses

Miss Ratio = 1 − Hit Ratio

### 6.3 Average Memory Access Time

Suppose a processor has two levels of memory:

- Level 1: Faster memory.
- Level 2: Slower memory.

Let:
- H = Hit ratio.
- T1 = Access time of Level 1.
- T2 = Access time of Level 2.

**Average Access Time:**

Average Access Time = H × T1 + (1 − H) × (T1 + T2)

**Example from PPT:**

Level 1:
- Access time = 0.01 μs
- Capacity = 1000 words.

Level 2:
- Access time = 0.1 μs
- Capacity = 100,000 words.

Hit ratio = 95% = 0.95.

Average Access Time:

= (0.95 × 0.01) + (0.05 × (0.01 + 0.1))

= 0.0095 + 0.0055

= **0.015 μs**

The average access time is much closer to the faster memory's access time.

This demonstrates the advantage of memory hierarchy.

### 6.4 Secondary Memory and Disk Cache

External nonvolatile memory is also known as:
- Secondary Memory
- Auxiliary Memory

Examples: Hard disk, magnetic disk, tape and optical storage.

**Disk Cache:**

A portion of main memory can be used as a buffer to hold data temporarily that is to be read out to disk.

Advantages:
1. A few large transfers of data can be used instead of many small transfers.
2. Improves disk performance and minimizes processor involvement.
3. Data can be retrieved rapidly from the software cache rather than slowly from the disk.

---

## 7. Cache Memory

### Definition

Cache memory is a small, high-speed memory that stores copies of portions of main memory.

It is designed to combine the memory access time of expensive, high-speed memory with the large memory size of less expensive, lower-speed memory.

### Need for Cache Memory

- Main memory is relatively large but slow.
- Cache memory is smaller but faster.
- The processor can access frequently used data more quickly from cache.
- It reduces the average memory access time.
- It improves overall system performance.

### Working of Cache Memory

1. The processor generates a memory address to read a word.
2. The cache checks whether the required word is present.
3. If the word is present, it is delivered directly to the processor.
4. This condition is called a Cache Hit.
5. If the word is not present, it is called a Cache Miss.
6. The block containing the required word is loaded from main memory into the cache.
7. The required word is then delivered to the processor.

Because of locality of reference, future references are likely to access the same memory location or other words in the fetched block.

### Cache Hit

When the required data is found in cache memory, it is called a cache hit.

Advantages:
- Faster data access.
- No system bus traffic is required in the illustrated organization.

### Cache Miss

When the required data is not found in cache memory, it is called a cache miss.

The required block is fetched from main memory and loaded into the cache.

### Cache Read Operation

The processor generates a Read Address (RA).

- If the word is contained in the cache, it is delivered to the processor.
- Otherwise, the block containing that word is loaded into the cache, and the word is delivered to the processor.

### Cache Hit and Cache Miss in Cache Organization

**When a cache hit occurs:**
- Data and address buffers are disabled.
- Communication takes place only between the processor and cache.
- There is no system bus traffic.

**When a cache miss occurs:**
- The desired address is loaded onto the system bus.
- Data are returned through the data buffer to both the cache and processor.

### Multiple Levels of Cache

Modern processors use multiple levels of cache:

- L1 Cache: Fastest and smallest.
- L2 Cache: Slower and typically larger than L1.
- L3 Cache: Slower and typically larger than L2.

---

## 8. Elements of Cache Design

The important elements of cache design include:

1. Cache addresses
2. Cache size
3. Mapping function
4. Replacement algorithms
5. Write policy
6. Line size
7. Number of caches

### 8.1 Cache Addresses

Virtual memory is a facility that allows programs to address memory from a logical point of view, without regard to the amount of main memory physically available.

When virtual memory is used:
- Machine instructions contain virtual addresses.
- A hardware Memory Management Unit (MMU) translates each virtual address into a physical address in main memory.

**Types of Cache Addresses**

**A. Logical Cache (Virtual Cache)**

- Stores data using virtual addresses.
- Processor accesses the cache directly without going through the MMU.
- Cache access speed is faster because the cache can respond before address translation.

Disadvantage:
- Different applications can use the same virtual address for different physical addresses.
- Cache must be flushed during each application context switch, or extra bits must be added to identify the virtual address space.

**B. Physical Cache**

- Stores data using main memory physical addresses.
- Address translation is performed before accessing the cache.

### 8.2 Cache Size

Cache size is an important design element.

The cache should be:
- Small enough so that the overall average cost per bit is close to that of main memory alone.
- Large enough so that the overall average access time is close to that of the cache alone.

Reasons for minimizing cache size:
1. Larger caches require more gates for addressing.
2. Larger caches tend to be slightly slower than smaller ones.
3. Available chip and board area limits cache size.
4. Cache performance depends on the nature of the workload.

There is no single optimum cache size for every application.

---

## 9. Mapping Function

Because there are fewer cache lines than main memory blocks, an algorithm is needed for mapping main memory blocks into cache lines.

The choice of mapping function dictates how the cache is organized.

There are three mapping techniques:

1. Direct Mapping
2. Associative Mapping
3. Set-Associative Mapping

### 9.1 Direct Mapping

**Definition:**

Direct mapping is the simplest technique that maps each block of main memory into only one possible cache line.

**Formula:**

i = j MODULO m

Where:
- i = Cache line number.
- j = Main memory block number.
- m = Number of lines in the cache.

**Working:**

- Each main memory block is assigned to a fixed cache line.
- The cache line is determined using the modulo operation.
- Multiple main memory blocks can map to the same cache line.
- A Tag is used to identify which main memory block currently occupies the cache line.

**Address Fields:**

A memory address is divided into three fields:

1. Tag
2. Line
3. Word

- Tag identifies the main memory block.
- Line identifies a particular cache line.
- Word identifies a particular word or byte within the block.

**Direct Mapping Summary:**

Address length = (s + w) bits

Number of addressable units = 2^(s+w)

Block size = Line size = 2^w

Number of blocks in main memory = 2^s

Number of cache lines = m = 2^r

Size of tag = (s − r) bits

**Advantages:**
- Simple implementation.
- Inexpensive.
- Fast access.

**Disadvantages:**
- A fixed cache location exists for every memory block.
- Two frequently used blocks may map to the same cache line.
- This can result in repeated swapping of blocks.
- Hit ratio may become low.

### Thrashing

Thrashing occurs when two different main memory blocks repeatedly map to the same cache line and are continually swapped in the cache.

This results in a low hit ratio.

### Victim Cache

A victim cache is a fully associative cache used to reduce the conflict misses of direct-mapped caches without affecting their fast access time.

Important points:
- It stores recently discarded cache blocks.
- It helps reuse discarded data if needed again.
- Typical size is 4 to 16 cache lines.
- It resides between the direct-mapped L1 cache and the next level of memory.

---

### 9.2 Associative Mapping

**Definition:**

Associative mapping permits each main memory block to be loaded into any line of the cache.

It overcomes the disadvantage of direct mapping by providing flexibility in placing blocks.

**Working:**

- Any main memory block can be placed in any cache line.
- The memory address is divided into two fields:
  1. Tag
  2. Word
- The Tag field uniquely identifies a block of main memory.
- The cache control logic simultaneously examines every line's Tag for a match.
- If a match is found, it is a cache hit.

**Associative Mapping Summary:**

Address length = (s + w) bits

Number of addressable units = 2^(s+w)

Block size = Line size = 2^w

Number of blocks in main memory = 2^s

Number of cache lines = Undetermined

Size of Tag = s bits

**Advantages:**
- Any memory block can be placed in any cache line.
- More flexibility in block replacement.
- Overcomes the fixed-location disadvantage of direct mapping.

**Disadvantages:**
- Complex circuitry is required.
- Tags of all cache lines must be examined simultaneously.
- Hardware implementation is more expensive.

---

### 9.3 Set-Associative Mapping

**Definition:**

Set-associative mapping is a compromise that exhibits the strengths of both direct and associative approaches while reducing their disadvantages.

**Working:**

- Cache consists of a number of sets.
- Each set contains a number of lines.
- A given main memory block maps to a particular set.
- The block can be loaded into any line within that set.

For example:

If each set contains 2 lines, it is called **2-way set-associative mapping**.

A given block can be placed in either of the two lines in only one set.

**Formulas:**

m = v × k

i = j MODULO v

Where:
- i = Cache set number.
- j = Main memory block number.
- m = Number of lines in the cache.
- v = Number of sets.
- k = Number of lines in each set.

**Address Fields:**

A memory address is divided into:

1. Tag
2. Set
3. Word

- Tag identifies the main memory block.
- Set identifies a particular cache set.
- Word identifies the word or byte within the block.

**Set-Associative Mapping Summary:**

Address length = (s + w) bits

Number of addressable units = 2^(s+w)

Block size = Line size = 2^w

Number of blocks in main memory = 2^s

Number of lines in each set = k

Number of sets = v = 2^d

Number of lines in cache = m = kv = k × 2^d

Size of cache = k × 2^(d+w) words or bytes

Size of Tag = (s − d) bits

**Advantages:**
- Combines the strengths of direct and associative mapping.
- Reduces the disadvantages of both approaches.
- Improves hit ratio over direct mapping.

**Disadvantage:**
- More complex than direct mapping.

**Important Cases:**

1. If v = m and k = 1, set-associative mapping reduces to direct mapping.
2. If v = 1 and k = m, set-associative mapping reduces to associative mapping.
3. Two-way set-associative mapping is a common organization.
4. Four-way set-associative mapping provides a modest additional improvement.

---

## 10. Comparison of Mapping Techniques

| Feature | Direct | Associative | Set-Associative |
|---|---|---|---|
| Placement | One fixed line | Any cache line | Any line in a particular set |
| Address fields | Tag, Line, Word | Tag, Word | Tag, Set, Word |
| Complexity | Simple | Complex | Moderate |
| Flexibility | Low | High | Moderate |
| Tag comparison | One selected line | All cache lines | Lines in selected set |
| Replacement | No choice | Required | Required |

**Remember:**
- Direct mapping = One fixed location.
- Associative mapping = Any location.
- Set-associative mapping = Any location within a particular set.

---

## 11. Replacement Algorithms

Once the cache has been filled, when a new block is brought into the cache, one of the existing blocks must be replaced.

For direct mapping, there is only one possible line for any particular block, so no choice is possible.

For associative and set-associative mapping, a replacement algorithm is needed.

To achieve high speed, the algorithm must be implemented in hardware.

### 11.1 Least Recently Used (LRU)

- It replaces the block in the set that has been in the cache longest with no reference to it.
- It assumes that recently used memory locations are more likely to be referenced again.
- It is one of the most effective replacement algorithms.
- It is the most popular replacement algorithm because of its simplicity of implementation.

### 11.2 First-In-First-Out (FIFO)

- It replaces the block in the set that has been in the cache longest.
- The block that entered first is replaced first.
- Easily implemented using a round-robin or circular buffer technique.

### 11.3 Least Frequently Used (LFU)

- It replaces the block that has experienced the fewest references.
- It can be implemented by associating a counter with each line.

### 11.4 Random Replacement

- A line is selected randomly from among the candidate lines.
- It does not depend on usage.
- Simulation studies show that random replacement provides only slightly inferior performance compared to usage-based algorithms.

### Comparison

| Algorithm | Replacement Basis |
|---|---|
| LRU | Least recently used block |
| FIFO | Block that entered first |
| LFU | Least frequently accessed block |
| Random | Randomly selected block |

---

## 12. Write Policy

When a block that is resident in the cache is to be replaced, two cases must be considered:

**Case 1:** If the old block has not been altered, it can be overwritten with a new block without first writing out the old block.

**Case 2:** If at least one write operation has been performed on a word in that cache line, main memory must be updated by writing the cache line back to the corresponding block in memory before bringing in the new block.

There are two major write policies.

### 12.1 Write Through

- It is the simplest technique.
- All write operations are made to main memory as well as to the cache.
- Main memory is always kept valid.
- Other processor-cache modules can monitor traffic to maintain consistency.

**Disadvantages:**
- Generates substantial memory traffic.
- May create a bottleneck.
- Every write operation also updates main memory.

### 12.2 Write Back

- It minimizes memory writes.
- Updates are made only in the cache.
- A Dirty Bit is associated with each cache line.
- When an update occurs, the dirty bit is set.
- When a block is replaced, it is written back to main memory only if the dirty bit is set.

**Disadvantages:**
- Portions of main memory may contain invalid data.
- Accesses by I/O modules must be allowed through the cache.
- Requires complex circuitry and may create a bottleneck.

### Difference Between Write Through and Write Back

| Write Through | Write Back |
|---|---|
| Updates cache and main memory | Updates only cache initially |
| Main memory is always valid | Main memory may contain outdated data |
| Generates more memory traffic | Minimizes memory writes |
| Simpler technique | More complex technique |
| Can create memory bottleneck | Requires dirty bit |

### 12.3 Cache Coherency

Cache coherency is a system property that ensures consistency of data among multiple caches and main memory.

**Problem:**

When multiple processors are attached to the same bus and each processor has its own local cache, changing a word in one cache may invalidate the corresponding word in other caches.

Even with write-through, other caches may contain invalid data.

**Approaches to Cache Coherency:**

1. **Bus Watching with Write Through**
   - Each cache controller monitors address lines.
   - It detects write operations to memory by other bus masters.
   - If another master writes to a location that also resides in the cache, that cache entry is invalidated.

2. **Hardware Transparency**
   - Additional hardware ensures that updates to main memory through cache are reflected in all caches.
   - If one processor modifies a word, matching words in other caches are also updated.

3. **Non-Cacheable Memory**
   - A portion of main memory shared by multiple processors is designated as non-cacheable.
   - Shared memory is never copied into the cache.
   - All accesses to this memory result in cache misses.

---

## 13. Line Size

Line size refers to the size of a block transferred between main memory and cache memory.

When a block of data is retrieved and placed in the cache, not only the desired word but also some number of adjacent words are retrieved.

### Effect of Increasing Block Size

Initially, as block size increases:
- More useful data are brought into the cache.
- Hit ratio increases because of locality of reference.
- Nearby memory locations are likely to be accessed in the near future.

However, when the block becomes too large:
- Hit ratio begins to decrease.
- Larger blocks reduce the number of blocks that fit into a cache.
- Each additional word is farther from the requested word.
- Newly fetched information may be less useful than the information that has to be replaced.

The relationship between block size and hit ratio is complex and depends on the locality characteristics of a particular program.

According to the PPT:
- 8 to 64 bytes is reasonably close to optimum for general systems.
- For HPC systems, 64-byte and 128-byte cache line sizes are most frequently used.

---

## 14. Multilevel Caches

As logic density has increased, it has become possible to have a cache on the same chip as the processor. This is called an **On-Chip Cache**.

### Advantages of On-Chip Cache

1. Reduces the processor's external bus activity.
2. Speeds up execution time.
3. Increases overall system performance.
4. Eliminates bus access when the requested instruction or data is found in the on-chip cache.
5. Cache accesses are faster because of shorter data paths.
6. The bus remains free to support other transfers.

### Two-Level Cache

The simplest multilevel organization is a two-level cache.

- L1 Cache: Internal cache.
- L2 Cache: External cache.

**Why is L2 Cache required?**

If the requested memory location is not found in L1 and there is no L2 cache, the processor must access main memory across the bus.

This results in poor performance because of slow bus speed and memory access time.

An L2 SRAM cache can quickly provide the missing information.

### Three-Level Cache

Modern processors may use three levels:

- L1 – Fastest and smallest.
- L2 – Larger and slower than L1.
- L3 – Larger and slower than L2.

The potential savings from L2 cache depend on the hit rates in both L1 and L2.

**Disadvantages of Multilevel Cache:**

It complicates cache design issues, including:
- Cache size.
- Replacement algorithm.
- Write policy.

---

## 15. Unified Versus Split Caches

### Unified Cache

A unified cache is a single cache used to store references to both instructions and data.

**Advantages:**

1. Higher hit rate for a given cache size because it balances the load between instruction and data fetches automatically.
2. Only one cache needs to be designed and implemented.

### Split Cache

A split cache consists of two separate caches:

1. Instruction Cache – Dedicated to instructions.
2. Data Cache – Dedicated to data.

Both exist at the same level, typically as two L1 caches.

**Advantages:**

1. Eliminates cache contention between the instruction fetch/decode unit and execution unit.
2. Improves performance in pipelining.
3. Instruction fetches and data accesses can take place independently.

**Important Trend:**

The trend is toward split caches at the L1 level and unified caches for higher levels.

### Difference Between Unified and Split Cache

| Unified Cache | Split Cache |
|---|---|
| Stores both instructions and data | Separate instruction and data caches |
| Balances instruction and data fetches | Dedicated caches for each |
| Higher hit rate for a given size (as described in PPT) | Eliminates cache contention |
| Only one cache is designed | Two separate caches are designed |
| May suffer from contention | Useful for pipelining |

---

## 16. Pentium 4 Cache Organization

The Pentium 4 processor provides an example of a multilevel cache organization.

### Main Points

- Pentium 4 has L1, L2 and L3 cache organization.
- L1 data cache is 16 KB.
- L1 data cache uses a line size of 64 bytes.
- It uses a four-way set-associative organization.
- Both L2 and L3 caches are eight-way set-associative.
- Both L2 and L3 have a line size of 128 bytes.

### Four Major Components of the Processor Core

**1. Fetch/Decode Unit**
- Fetches program instructions in order from the L2 cache.
- Decodes instructions into a series of micro-operations.
- Stores the results in the L1 instruction cache.

**2. Out-of-Order Execution Logic**
- Schedules execution of micro-operations based on data dependencies and resource availability.
- Micro-operations may be executed in a different order from the instruction stream.
- Also schedules speculative execution of micro-operations that may be required in the future.

**3. Execution Units**
- Execute micro-operations.
- Fetch required data from the L1 data cache.
- Temporarily store results in registers.

**4. Memory Subsystem**
- Includes L2 and L3 caches and the system bus.
- Accesses main memory when L1 and L2 caches have a cache miss.
- Also accesses system I/O resources.

### Write Policy in Pentium 4

- The data cache employs a write-back policy.
- Data are written to main memory only when they are removed from the cache and there has been an update.
- Pentium 4 can also be dynamically configured to support write-through caching.

### Important Pentium 4 Instructions

**INVD:**
- Invalidates (flushes) the internal cache memory.
- Signals the external cache, if any, to invalidate.

**WBINVD:**
- Writes back and invalidates the internal cache.
- Then writes back and invalidates the external cache.

---

# QUICK REVISION – IMPORTANT FORMULAS

1. Number of addressable units:

   N = 2^A

2. Memory cycle time:

   Memory Cycle Time = Access Time + Additional Time

3. Transfer rate:

   Transfer Rate = 1 / Cycle Time

4. Hit ratio:

   H = Cache Hits / Total Memory Accesses

5. Miss ratio:

   Miss Ratio = 1 − H

6. Average access time (two-level memory):

   Tavg = H × T1 + (1 − H) × (T1 + T2)

7. Direct mapping:

   i = j MODULO m

8. Set-associative mapping:

   m = v × k

   i = j MODULO v

9. Direct mapping tag size:

   Tag = s − r bits

10. Associative mapping tag size:

    Tag = s bits

11. Set-associative mapping tag size:

    Tag = s − d bits

---

# IMPORTANT TOPICS FOR EXAM REVISION

Give priority to these topics while preparing:

1. Characteristics of Memory Systems.
2. Four Methods of Accessing Units of Data.
3. Access Time, Memory Cycle Time and Transfer Rate.
4. Memory Hierarchy and Locality of Reference.
5. Cache Memory – Definition and Working.
6. Cache Hit, Cache Miss and Hit Ratio.
7. Direct Mapping with formula and address fields.
8. Associative Mapping with formula and address fields.
9. Set-Associative Mapping with formula and address fields.
10. Comparison of the Three Mapping Techniques.
11. Replacement Algorithms – LRU, FIFO, LFU and Random.
12. Write Through vs Write Back.
13. Cache Coherency and its approaches.
14. Line Size and its effect on Hit Ratio.
15. Multilevel Caches.
16. Unified vs Split Caches.
17. Pentium 4 Cache Organization.

**End of Chapter 4 – Cache Memory**
:::
