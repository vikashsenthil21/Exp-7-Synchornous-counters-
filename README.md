# Exp-6-Synchornous-counters - up counter and down counter 
## AIM : 
To implement 4 bit up and down counters and validate  functionality.

##  COMPONENTS REQUIRED : 
#### HARDWARE REQUIRED : PC, Cyclone II , USB flasher.

#### SOFTWARE REQUIRED  :  Quartus prime.

## THEORY :
### UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



### DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
## Procedure :
1. Use module projname(input,output) to start the Verilog programmming.

2. Assign inputs and outputs using the word input and output respectively.

3. Use defined keywords like wire,assign and required logic gates to represent the boolean expression.

4. Use each output to represnt onre for differnce and the other for borrow.

5. End the verilog program using keyword endmodule.

## PROGRAM :
```

Developed By : VIKASH S

Register Number :  212222240115
```
### Up Counter :
```
module upcounter(D,C,B,A,clk);
output reg D,C,B,A;
input clk;
always@(posedge clk)
begin
	D=(C&B&A)^D;
	C=(B&A)^C;
	B=(A^B);
	A=1^A;
end
endmodule
```
### Down Counter :
```
module downcounter(clk,A);
input clk;
output reg [3:0]A;
always @(posedge clk)
begin
A[3]=((~A[2])&(~A[1])&(~A[0]))^A[3];
A[2]=((~A[1])&(~A[0]))^A[2];
A[1]=(~A[0])^A[1];
A[0]=1^A[0];
end
endmodule
```

##  RTL DIAGRAM :
### Up Counter :
![image](https://github.com/vikashsenthil21/Exp-7-Synchornous-counters-/assets/119433834/ba129d75-08c1-4e34-84f4-67914a3d1fb0)


### Down Counter :
![image](https://github.com/vikashsenthil21/Exp-7-Synchornous-counters-/assets/119433834/d3edcba7-b451-4c92-b5ef-b2f0753f7ca9)


## TIMING DIAGRAMS OR WAVEFORM :
### Up Counter :

![image](https://github.com/vikashsenthil21/Exp-7-Synchornous-counters-/assets/119433834/d882c6df-c6e6-47d3-ac55-fd03e8b379e6)
### Down Counter :
![image](https://github.com/vikashsenthil21/Exp-7-Synchornous-counters-/assets/119433834/ab302de4-2841-41eb-a3ce-dfb795345d55)

##  TRUTH TABLE :
### Up Counter :

![image](https://github.com/vikashsenthil21/Exp-7-Synchornous-counters-/assets/119433834/fff3d6bb-b4ba-4a78-9c6c-79c32defd566)



### Down Counter :
![image](https://github.com/vikashsenthil21/Exp-7-Synchornous-counters-/assets/119433834/71a60433-860d-44e5-8bb1-e7fb9785b335)


## RESULTS :
Thus Synchornous counters up counter and down counter circuit are studied and the truth table for different logic gates are verified.
