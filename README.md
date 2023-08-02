# AHB-TO-APB-BRIDGE
The AHB to APB bridge is a hardware device that provides an interface between the high-speed AHB bus and the low-power APB bus. It allows devices that are connected to the APB bus to communicate with devices that are connected to the AHB bus.

Advanced High-performance Bus (AHB):
The AMBA AHB is for system modules with high performance and high clock frequencies. The high-performance system backbone bus is the AHB. With the aid of AHB, low-power peripheral macrocell functions can be effectively connected to processors, on-chip memories, and off-chip external memory interfaces. Additionally, AHB is intended to guarantee usability in an effective design flow employing synthesis and automated test methods.
Advanced System Bus (ASB):
For high-performance system modules, there is the AMBA ASB. The AMBA ASB is an alternate system bus that can be used in situations where AHB's high-performance capabilities are not necessary. Additionally, ASB enables the effective coupling of CPUs, on-chip memories, and off-chip external memory interfaces with peripheral macrocell operations that consume less power.
Advanced Peripheral Bus (APB):
Low-power peripherals should use the AMBA APB. AMBA APB is designed to use the least amount of power possible and provide a simpler interface to support peripheral operations. It is possible to employ APB in conjunction with either system bus iteration.

The general architecture appears as follows:

![image](https://github.com/saikrishnareddy2002/-AHB-TO-APB-BRIDGE/assets/127223195/143a642a-04af-4ec0-b63e-218755b63a39)

Basic Terminology:

Bus transition
A read or write action of a data item, which may require one or more bus cycles, is referred to as an AMBA ASB or AHB bus transfer. A completion answer from the addressed slave ends the bus transfer. A read or write operation of a data item is an AMBA APB bus transfer, which always necessitates two bus cycles.

Bus cycle
For the purposes of the AMBA AHB or APB protocol specifications, a bus cycle is a fundamental unit of one bus clock period and is defined from rising-edge to rising-edge transitions.

Burst Operation 
A burst operation is described as one or more data transactions with a constant transaction width to an additional region of address space that are started by a bus master. The width of transmission (byte, halfword, or word) determines the increment step per transaction. The APB does not support burst operations.


Basic Implementation Tools:
•	HDL Used : Verilog
•	Simulator Tool Used: ModelSIM
•	Synthesis Tool Used: Quartus Prime
•	Family: Cyclone V
•	Device: 5CSXFC6D6F31I7ES


Implementation:
Objective:
To design and simulate a synthesizable AHB to APB bridge interface using Verilog and run single read and single write tests using AHB Master and APB Slave testbenches. The bridge unit converts system bus transfers into APB transfers and performs the following functions:
•	Latches the address and holds it valid throughout the transfer.
•	Decodes the address and generates a peripheral select, PSELx. Only one select signal can be active during a transfer.
•	Drives the data onto the APB for a write transfer.
•	Drives the APB data onto the system bus for a read transfer.
•	Generates a timing strobe, PENABLE, for the transfer
•	Can implement single read and write operations successfully.

The diagram below shows the interface:
![image](https://github.com/saikrishnareddy2002/-AHB-TO-APB-BRIDGE/assets/127223195/6380ac83-cd01-4b58-9e4a-8639284feeb5)

Design Modules:
AHB Slave Interface
Transfer requests made by system bus masters are answered by an AHB bus slave. When deciding how to react to a bus transfer, the slave employs an HSELx choose signal from the decoder. The bus master will produce any additional signals needed for the transfer, including address and control information.
APB Controller:
The address decoding logic that creates the APB peripheral select lines and the state machine that controls the creation of the APB and AHB output signals are both included in the AHB to APB bridge.

Note:
The design files are attached in the repository along with the AHB Master and APB Slave which generates the appropriate signals. Only the Bridge is synthesizable and other modules are used as testbenches only to generate the necessary read/write operations. Below are the screenshots from the synthesis and the simulator tool

Conclusion: AHB2APB Bridge and the Future of System Design
In conclusion, the AHB2APB Bridge is a critical component in modern system design. Its ability to improve communication between different bus architectures and increase system performance makes it an invaluable tool for designers and engineers alike.
Throughout this presentation, we have explored the benefits of using an AHB2APB Bridge, discussed key design considerations, and presented performance analysis and a real-world case study. We hope that this information has been informative and engaging, and that you leave with a better understanding of the importance of the AHB2APB Bridge in modern system design.

Simulation Results:
Read only:

![image](https://github.com/saikrishnareddy2002/-AHB-TO-APB-BRIDGE/assets/127223195/b1e5aa01-61d0-483a-8549-903906ce83ef)


Write only:
![image](https://github.com/saikrishnareddy2002/-AHB-TO-APB-BRIDGE/assets/127223195/076b8e49-0500-404f-a141-5992012fade4)


Burst write wrap:
![image](https://github.com/saikrishnareddy2002/-AHB-TO-APB-BRIDGE/assets/127223195/6d5c8448-c7e6-4dd6-a60d-f5603240d41f)

Burst read wrap:
![image](https://github.com/saikrishnareddy2002/-AHB-TO-APB-BRIDGE/assets/127223195/8ac7f1bc-c6c2-403b-89d3-1aa611981841)








