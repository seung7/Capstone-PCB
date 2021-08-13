# PCB for Capstone Project

## Goal
Our Capstone Project MUP(Monitoring Unoccupied Property) should be able to work when a power outrage is happened. To achieve this, we require a PCB that can automatically switch to the battery power when the power outrage is happened. In other words, the PCB should work as UPS(Uninterruptible Power Supply)

## Requirements
1. PCB should deliver minimum of 5V, 2.5A (12.5W) to MUP 

| Components in MUP    | Amp           |
| ------------- |:-------------:| 
| Raspberry Pi 4B at maximum load (400% CPU Usages)     | 1280mA
| Camera      | 400mA      | 
| MangOH Yellow | 500mA      |
| Keyboard & Mouse | 100mA |
| HDMI | 50mA|
| | |
| Total| 2330mA |

2. PCB should be able to recharge the custom 18650 battery pack: https://www.batteryspace.com/custom-li-ion-18650-battery-3-635v-28ah-101-78wh-7a-rate-2x4s-s-inr18650-mj1.aspx  and MUP in a same time, when the 5.1V 3A wall power adapter: https://www.raspberrypi.org/products/type-c-power-supply/ is plugged in
3. PCB should use USB-C as both input and output

## Open Source 
We have found the Open Source PCB created by CRAIG PEACOCK, which satisfies our requirements:
https://workspace.circuitmaker.com/Projects/Details/Craig-Peacock-4/5V-Uninterruptable-Power-Supply-USB#sectionTeam

## Modification
1. Change of R1. 

We need the total input current to be 3.5A so that when the AC adaptor is pluged, MUP can draw a full 2.5A while the remaining 1A will be used to charge the battery at the same time. The current of the circuit can be altered by R1. By modifying R1 from 0.01ohm to 0.007ohm, the circuit can provide 0.025v/0.007 = 3.5A rather than 0.025v/0.01 = 2.5A.

2. Bigger battery pack.

The original design uses two 18650 batteries, that gives 4400mAh. That would only last for 4400mAh/2330mA = 1.8 hours. However our MUP should be ready for power outrages more than 6 hours. For that reason we have purchased 28000mAh customized battery pack providing 28000mAh/2330mA = 12 hours. To establish the connection, the battery's wires connected to its terminals are soldered into the PCB like the image below:



## Result
Our Raspberry Pi did not lose the power when we turn off the AC power outlet swtich. Our PCB successfully switches the power from the wall outlet to the battery pack.

<p align="center">
   <img src="Video_and_Images/PMS_Animated_GIF.gif">
</p>
