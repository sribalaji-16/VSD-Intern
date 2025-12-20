# Task 1:Environment Setup and RISC-V Reference Validation
### The complete workflow was executed using GitHub Codespace.

This repository logs the configuration of a RISC-V development workspace and the verification of the toolchain using the Spike simulator. It also covers preliminary tasks related to the VSD FPGA lab.  
We need to fork and open the repo in new codespace to do it. 

System Configuration
- Platform: GitHub Codespaces
- OS: Linux   

<img width="1855" height="911" alt="Screenshot From 2025-12-20 11-04-06" src="https://github.com/user-attachments/assets/b82f16f8-6b6d-4c49-bf47-a1a761f67b7b" />

#### Verify the Setup
```sh
riscv64-unknown-elf-gcc --version
spike --version
iverilog -V
```  
<img width="1856" height="907" alt="Screenshot From 2025-12-20 08-38-24" src="https://github.com/user-attachments/assets/68ead6b2-cb5e-46ee-b5eb-1002f3b3eaa4" />

## Run Your First Program (in linux using gcc compiler)
Compile the program:

```sh
gcc sum1ton.c
```
Run the output file
```sh
./a.out
```
Expected output:
```sh
Sum from 1 to 9 is 45
```  

<img width="1855" height="911" alt="Screenshot From 2025-12-20 11-03-09" src="https://github.com/user-attachments/assets/81beff26-9678-44d1-8537-226b31434cbb" />  

## Run Your First Program (using riscv gcc compiler)

Go to the samples folder.

Compile the program:
```sh
riscv64-unknown-elf-gcc -o sum1ton.o sum1ton.c
```
Run it with Spike:
```sh
spike pk sum1ton.o
```
Expected output:
```sh
Sum from 1 to 9 is 45
```  

<img width="1854" height="963" alt="Screenshot From 2025-12-20 08-46-36" src="https://github.com/user-attachments/assets/553051e8-c963-4a93-bcb8-335100d09a1c" />  


<img width="1854" height="963" alt="Screenshot From 2025-12-20 08-47-09" src="https://github.com/user-attachments/assets/6c5d5d26-923c-406e-89c1-fe948daee5be" />



# Working with GUI Desktop (noVNC) – Advanced

In your Codespace, click the PORTS tab.  

<img width="1856" height="907" alt="Screenshot From 2025-12-20 08-35-29" src="https://github.com/user-attachments/assets/d6e3f95e-335a-4fef-a0e3-78f93c840752" />

Look for the forwarded port named noVNC Desktop (6080).  

Click the Forwarded Address link.  

A new browser tab opens with a directory listing. Click vnc_lite.html.  

<img width="1854" height="963" alt="Screenshot From 2025-12-20 08-49-36" src="https://github.com/user-attachments/assets/b6e23d13-1868-41c1-8885-2c029aae69ed" />
The Linux desktop appears in your browser.


## Open a Terminal Inside the Desktop

Navigate to the Sample Programs  

In the terminal, go to the workspace and then to the samples folder: 
```sh
cd /workspaces/vsd-riscv2
cd samples
ls -ltr
```
You should see files like sum1ton.c, 1ton_custom.c, load.S, and Makefile.  

<img width="1854" height="963" alt="Screenshot From 2025-12-20 08-53-07" src="https://github.com/user-attachments/assets/265e3846-ace1-4578-b91e-38916a6e7b3e" />

## Compile and Run Using Native GCC (x86)
Compile the program:
```sh
gcc sum1ton.c
```
Run the output file
```sh
./a.out
```
Expected output:
```sh
Sum from 1 to 9 is 45
```   

<img width="1854" height="963" alt="Screenshot From 2025-12-20 08-53-51" src="https://github.com/user-attachments/assets/4f98bae3-a1a6-4eb8-a199-9d2c98742298" />

## Compile and Run Using RISC-V GCC and Spike
Now compile the same program for RISC-V and run it on the Spike ISA simulator:
Compile the program:
```sh
riscv64-unknown-elf-gcc -o sum1ton.o sum1ton.c
```
Run it with Spike:
```sh
spike pk sum1ton.o
```
Expected output:
```sh
Sum from 1 to 9 is 45
```  

<img width="1854" height="963" alt="Screenshot From 2025-12-20 08-56-30" src="https://github.com/user-attachments/assets/4c4e98d5-ab11-483a-8788-72103818f57e" />



## Edit my own c program using RISC-V gcc and Spike

<img width="1854" height="965" alt="Screenshot From 2025-12-20 11-40-06" src="https://github.com/user-attachments/assets/d174f9c3-17f7-44e8-a9a2-a4ca439dad97" />

<img width="1854" height="965" alt="image" src="https://github.com/user-attachments/assets/3b022413-a68e-4e7a-8103-95908a2e071c" />


# Clone and Run VSDFPGA Labs

## Hardware Connections (VSDSquadron FPGA mini)
| Source Component | Source Pin/Port | Destination Component       | Destination Pin/Port |
|------------------|-----------------|------------------------------|----------------------|
| CH340            | TX              | [VSDFPGA Board](https://www.vlsisystemdesign.com/vsdsquadronfm/)  | 3                    |
| CH340            | RXD             | [VSDFPGA Board](https://www.vlsisystemdesign.com/vsdsquadronfm/)  | 4                    |
| [VSDFPGA Board](https://www.vlsisystemdesign.com/vsdsquadronfm/)       | GND             | FPGA Board                   | 23                   |
| CH340            | 3.3V            | CH340                        | VCC                  |

- Connect the [VSDSquadron FPGA mini](https://www.vlsisystemdesign.com/vsdsquadronfm/) board to one USB port.
- Connect the CH340 module to another USB port.

## Setup 
Once the RISC-V reference flow works, clone the FPGA labs repository inside the same Codespace:
```sh
git clone https://github.com/vsdip/vsdfpga_labs.git
cd vsdfpga_labs
```

## Executing Risc-v logo program on CodeSpace

Move to the cloned repo of vsdfpga_labs to this `Firmware` directory using the given below
```sh
cd vsdfpga_labs/basicRISCV/Firmware/
```
<img width="1854" height="965" alt="Screenshot From 2025-12-20 16-13-42" src="https://github.com/user-attachments/assets/f7073506-5521-4fb8-9dbb-7e0c31163232" />


Then run the risc_logo.c file (or edit the changes iff required) like how we used to do previously 

<img width="1854" height="965" alt="Screenshot From 2025-12-20 16-31-13" src="https://github.com/user-attachments/assets/2947ae37-1a11-448f-9001-36cb7ec573d5" />

<img width="1854" height="965" alt="Screenshot From 2025-12-20 16-31-24" src="https://github.com/user-attachments/assets/30e5e73f-81bc-48a7-b492-1d0b8fc20252" />



## `Building & Flashing`
Review the RISC-V logo code (do not modify):
   ```bash
   cd vsdfpga_labs/basicRISCV/Firmware
   nano riscv_logo.c  
   make riscv_logo.bram.hex
   ```
You should see the below messages
<img width="1845" height="800" alt="Screenshot From 2025-12-20 17-10-40" src="https://github.com/user-attachments/assets/aa73c036-586f-445b-92e7-42c5a624d689" />



Build the firmware and FPGA bitstream:
   ```bash
   cd ../RTL
   make clean
   make build
   ```

<img width="1856" height="1047" alt="Screenshot From 2025-12-20 17-14-42" src="https://github.com/user-attachments/assets/d76c4d9c-66d6-4ead-983d-c2b312c8953e" />


Flash to FPGA:
   ```bash
   sudo make flash
   ```

<img width="1856" height="1047" alt="Screenshot From 2025-12-20 17-18-20" src="https://github.com/user-attachments/assets/266e4d7c-3034-4836-8043-30e3d8b0e761" />

![VSDSquadron FPGA mini](https://github.com/user-attachments/assets/2a5c2601-ca20-4462-bb87-fb3f2bf31e3f)



https://github.com/user-attachments/assets/4b6e8b9b-c5ce-49ac-80e4-9bdace2b974f

## Running the Lab
Open the serial terminal:
   ```bash
   make terminal
   ```
<img width="1856" height="1047" alt="Screenshot From 2025-12-20 17-45-44" src="https://github.com/user-attachments/assets/32be75d3-0650-4d1d-8ffc-660b540fd3fd" />


# Conclusion
The workspace was initialized and fully verified within a GitHub Codespaces Linux environment.

Validation Task
- Source Repository: vsd-riscv-v2
- Directory: samples/

To confirm the stability of the toolchain and environment, a standard RISC-V reference program was successfully compiled and simulated using Spike.
