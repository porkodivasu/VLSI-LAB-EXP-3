SIMULATION AND IMPLEMENTATION OF MULTIPLIER
**AIM: **
 To simulate and synthesis multiplier using Xilinx ISE.

**APPARATUS REQUIRED:**
Xilinx 14.7
Spartan6 FPGA
  
**PROCEDURE:**
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

**Logic Diagram**
2 bit Multiplier

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/7713750f-65e6-41c0-8082-5005eac4031c)

**4 Bit Multiplier**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/d95215dd-8cf1-4e08-93cc-96adfdd7fbdc)


**Verilog code**
2 bit multiplier:

```
module ha(a,b,sum,c);
input a,b;
output sum,c;
xor g1(sum,a,b);
and g2(c,a,b);
endmodule
module multiplier(a,b,c);
input [1:0]a,b;
output[3:0]c;
wire w1;
and g1(c[0],b[0],a[0]);
and g2(c[0],b[0],a[0]);
ha ha1(a[0]&b[1],a[1]&b[0],c[1],w1);
ha ha2(a[1] &b[1],w1,c[2],c[3]);
endmodule
```

4 bit multiplier:

```
module multiplier4_4(z,a,b);
input [3:0]a,b;
output [7:0]z;
wire w1,w2,w3,w4,w5,w6,w7,w8,w9,w10,w11,w12,w13,w14,w15,w16,w17;
and a1(z[0],a[0],b[0]);
HalfAdder h0(z[1],w1,a[1]&b[0],a[0]&b[1]);
fulladder f0(w2,w3,w1,a[2]&b[0],a[1]&b[1]);
fulladder f1(w4,w5,w3,a[3]&b[0],a[2]&b[1]);
HalfAdder h1(w6,w7,w5,a[3]&b[1]);
HalfAdder h2(z[2],w8,w2,a[0]&b[2]);
fulladder f2(w9,w10,w8,w4,a[1]&b[2]);
fulladder f3(w11,w12,w10,w6,a[2]&b[2]);
fulladder f4(w13,w14,w12,w7,a[3]&b[2]);
HalfAdder h3(z[3],w15,w9,a[0]&b[3]);
fulladder f5(z[4],w16,w11,w15,a[1]&b[3]);
fulladder f6(z[5],w17,w16,w13,a[2]&b[3]);
fulladder f7(z[6],z[7],w17,w14,a[3]&b[3]);
endmodule
module HalfAdder(sum,carry,a,b);
input a,b;
output sum,carry;
xor (sum,a,b);
and (carry,a,b);
endmodule
module fulladder(sum,carry,a,b,c);
input a,b,c;
output sum,carry;
wire [3:1]w;
xor g1(w[1],a,b);
xor g2(sum,w[1],c);
and g3(w[2],a,b);
and g4(w[3],w[1],c);
or g5(carry,w[3],w[2]);
endmodule
```



**Output Waveform**


2 bit multiplier:

![Screenshot (87)](https://github.com/porkodivasu/VLSI-LAB-EXP-3/assets/160757120/8da705ff-42aa-4c1c-bd9d-a6765d051ce7)

4 bit multiplier:

![Screenshot (89)](https://github.com/porkodivasu/VLSI-LAB-EXP-3/assets/160757120/46bbf351-4150-40b4-8ef2-a754e49a4a36)



**Result**

Thus,the simulation and synthesis of multipliers by using vivado has been successfully excecuted and verified.


