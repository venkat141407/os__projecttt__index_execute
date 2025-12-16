Distributed File System (DFS) Simulator
This is a front-end simulation of a distributed file system built using HTML, CSS, and vanilla JavaScript. It uses the browser's localStorage to persist the state of the cluster, nodes, and file chunks, allowing users to visualize data replication, node failures, and automatic repair mechanisms without a backend server.

✨ Features
File Storage Simulation: Upload or paste text content which is then split into configurable chunks.

Configurable Parameters: Set the Replication Factor (how many copies of each chunk exist) and the Number of Nodes in the cluster.

Data Distribution: Simulates the round-robin distribution of file chunks across active nodes to meet the specified replication factor.

Cluster Monitoring: The execution page displays the state of all nodes (Online/Offline) and the number of chunks stored on each.

Failure Simulation: Manually fail or recover individual nodes, or simulate a random node failure.

Data Durability (Repair): A dedicated repair function identifies under-replicated chunks (chunks that lost replicas due to node failure) and re-replicates them onto available, healthy nodes.

File Reconstruction: Reconstruct the original file from the available chunks on the cluster.

🚀 Setup and Installation
This project requires no installation and runs directly in any modern web browser.

Create a new directory (e.g., dfs-simulator).

Save the first code block (Frontend) as index.html in this directory.

Save the second code block (Execution / Simulator) as execute.html in the same directory.

Open the index.html file in your web browser.

💡 How to Use
1. The Frontend (index.html)
This page is for configuration and initiating the storage process.

File/Text Input: You can either click "Text file input" to upload a .txt file or "Or paste text to store" in the provided textarea.

Replication Factor: Select how many copies of each chunk should be stored (e.g., 2 is selected by default).

Number of Nodes: Select the size of your simulated cluster (e.g., 4 is selected by default).

Chunk Size (chars): Define the size of the piece of text each chunk will hold.

Store File (Simulate): Splits the input text, distributes the replicas across the nodes, and opens the Execution Page in a new tab.

Reset Simulation: Clears all cluster data and stored files from the browser's localStorage.

2. The Execution / Simulator (execute.html)
This page allows you to interact with and observe the simulated DFS state.

A. Cluster State
Node Grid: Each node is displayed with its ID, status (ONLINE/OFFLINE), and the total number of chunks it holds.

Node Toggles: Click the "Fail" or "Recover" button next to any individual node to manually change its state.

B. Simulating Failures and Repair
Click "Simulate Random Node Failure" to take an arbitrary alive node offline.

Observe the Chunk Count on the remaining online nodes. (The total number of available replicas for certain chunks has now decreased, making them "under-replicated").

Click "Repair Under-Replicated". The system checks the required replication level and copies the missing chunks from the existing alive replicas to new alive and available nodes.

Click "Simulate Recover" to bring all failed nodes back online. Note that a recovered node does not immediately receive the chunks it missed during its downtime unless you trigger a repair process.

C. File Operations
Inspect: Shows a detailed list of all chunks belonging to the file and which nodes currently hold their replicas.

Reconstruct: Attempts to piece the file back together by fetching one copy of each chunk from any alive node. If the system fails to find a single copy of any chunk (meaning replication was too low and too many nodes failed), it will alert the missing chunk IDs.
