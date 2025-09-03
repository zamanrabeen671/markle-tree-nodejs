# 🌳 Merkle Tree

A **Merkle Tree** is a data structure used in **computer science** and **cryptography** to efficiently and securely verify the **integrity** and **consistency** of large datasets.  
It is a **binary tree** where:

- **Leaf nodes** store cryptographic hashes of data blocks.
- **Non-leaf nodes** store the hash of their child nodes.
- The **root node** (Merkle Root) is a single hash summarizing the entire dataset.

---

## 📌 Concepts of a Merkle Tree

### 🔑 1. Hashing
- Relies on **cryptographic hash functions** (e.g., `SHA-256`) to create fixed-length outputs.
- Even a **small change** in data results in a **completely different hash**.

![Hashing](image-1.png)

---

### 🌿 2. Leaf Nodes
- The bottom level of the tree.
- Each leaf = hash of a **data block** (e.g., a transaction in a blockchain).
- Example:  
  - Data blocks = `D1, D2, D3, D4`  
  - Leaf nodes = `H1 = hash(D1), H2 = hash(D2), H3 = hash(D3), H4 = hash(D4)`

---

### 🌲 3. Non-Leaf Nodes
- Each parent node = hash of the **concatenated hashes of its children**.  
- Example:  
  - `H12 = hash(H1 + H2)`  
  - `H34 = hash(H3 + H4)`

---

### 🏔️ 4. Root Node (Merkle Root)
- The **topmost node** of the tree.
- Represents the **entire dataset** in one compact hash.
- Used for **verification** in blockchain and distributed systems.

---

### 🧩 5. Binary Structure
- Merkle Trees are typically **binary trees**.
- If the number of data blocks is **odd**, the last hash is **duplicated** to keep the structure balanced.

---

## ⚙️ How a Merkle Tree Works

Steps to construct a Merkle Tree:

1. **Divide** the dataset into smaller blocks (e.g., transactions or file chunks).
2. **Hash** each block to create leaf nodes.
3. **Pair** the hashes and compute parent node hashes.
4. **Repeat** until only one hash remains → the **Merkle Root**.

---

### 📖 Example
- Data Blocks: `D1, D2, D3, D4`
- Leaf Hashes:  
  - `H1 = hash(D1)`  
  - `H2 = hash(D2)`  
  - `H3 = hash(D3)`  
  - `H4 = hash(D4)`
- Parent Hashes:  
  - `H12 = hash(H1 + H2)`  
  - `H34 = hash(H3 + H4)`
- Merkle Root:  
  - `HR = hash(H12 + H34)`

---

## 🏗️ Merkle Tree Construction Algorithm

**Input**  
- A list of data blocks (e.g., `[D1, D2, D3, D4]`).  
- A cryptographic hash function (e.g., `SHA-256`).  

**Steps**
1. **Leaf Node Creation**  
   - For each block `Di`, compute `Hi = SHA256(Di)`.

2. **Handle Odd Number of Hashes**  
   - If odd, **duplicate the last hash** to maintain pairs.

3. **Pairing & Hashing**  
   - Pair consecutive hashes → `(H1, H2), (H3, H4)`  
   - Compute parent hashes:  
     - `H12 = SHA256(H1 + H2)`  
     - `H34 = SHA256(H3 + H4)`

4. **Iterate Up the Tree**  
   - Use parent hashes as the new list.  
   - Repeat until only one hash (the **Merkle Root**) remains.

---

### ⚠️ Edge Cases
- **Empty Input** → return `null` or error.  
- **Single Block** → Merkle Root = hash of that block.  
- **Odd Number of Hashes** → duplicate last hash.  

---

## 🎯 Output
- **Merkle Root** → a single hash summarizing all data blocks.  
- Optionally, store the **entire tree structure** for verification/proof generation.  

![Merkle Root](image-5.png)

---
