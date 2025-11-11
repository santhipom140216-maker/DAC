# INTERFACING DAC WITH 8086 KIT AND GENERATING SAWTOOTH AND SQUARE WAVEFORMS

## AIM
To write an assembly language program in 8086 to generate Sawtooth and Square waveforms using DAC.

---

## APPARATUS REQUIRED

| S. No | Item              | Specification   | Quantity |
|-------|------------------|-----------------|----------|
| 1     | Microprocessor kit | 8086            | 1        |
| 2     | Power Supply      | +5 V DC, +12 V DC | 1      |
| 3     | DAC Interface board | -              | 1        |

---

## ALGORITHM

### Measurement of Analog Voltage
1. Send the digital value to DAC.  
2. Read the corresponding analog value at its output.  

### Waveform Generation

#### Square Waveform
1. Send low value (00) to the DAC.  
2. Introduce suitable delay.  
3. Send high value to DAC.  
4. Introduce delay.  
5. Repeat the above procedure.  

#### Sawtooth Waveform
1. Load low value (00) to accumulator.  
2. Send this value to DAC.  
3. Increment the accumulator.  
4. Repeat step (ii) and (iii) until accumulator value reaches FF.  
5. Repeat the above procedure from step 1.  

---

## PROGRAMS

# 8086 Assembly Programs – DAC Interfacing

## Program: Square Wave

| Memory Location | Program     | Comments                          |
|-----------------|-------------|-----------------------------------|
| 1000            | MOV AL,00H  | Load 00H in Accumulator           |
| 1003            |  OUT 0C8H,AL | Send through output port         |
| 1005            |  CALL DELAY(1100)  | CALL PROGRAM TO 1100      |
| 1008            |  MOV AL,0FFH |   Load 00H in Accumulator       |
| 100A            |   OUT 0C8H,AL|  Send through output port       |
| 100D            |  CALL DELAY(1100) | CALL PROGRAM TO 1100       |


| Memory Location | Program     | Comments                          |
|-----------------|-------------|-----------------------------------|
| 1100            | MOV CX,0505  | Load 0505H in Accumulator           |
| 1103            |  DEC CX | Decrement CX        |
| 1105           |  JNZ 1104  | RPEAT UNTILL ZERO      |
| 1108            |   RET |   RETURN TO MAIN PROGRAM      |


# Program: Sawtooth wave

## Assembly Program

| Memory Location | Program Instruction   | Comments                        |
|-----------------|-----------------------|---------------------------------|
| `1000`          | `START: MOV AL,00H`  | Load `00H` in accumulator       |
| `1003`          | `LOOP : OUT 0C8H,AL` | Send through output port        |
| `1005`          | `INC AL`             | Increment contents of accumulator |
| `1007`          | `JNC LOOP`           | Jump if no carry (continue loop) |
| `1009`          | `JMP START`          | Go to starting location         |

---

## Tabulation

| Waveform  | Amplitude | Time period | 
|-----------|-----------|-------------|
| Sawtooth  |  8.08V    |     1.642ms | 
| Square    |  9.60V    |     6.052ms |
---

## Model Graph

### SQUARE WAVE
![WhatsApp Image 2025-09-19 at 20 21 28_7aff63fa](https://github.com/user-attachments/assets/9dd2f4f9-0b53-48de-be26-227e830ad63e)

### SAWTOOTH WAVE
![WhatsApp Image 2025-09-19 at 20 21 48_95ddcb1d](https://github.com/user-attachments/assets/402c81a8-58b4-40a8-b3f3-a47c08afa61a)


## OUTPUT IMAGE OF DAC(SAWTOOTH WAVE FROM DSO AND SQUARE WAVE FROM DSO)
### SQUARE WAVE

<img width="1028" height="505" alt="image" src="https://github.com/user-attachments/assets/2aeffa4a-6b62-49bf-94be-6e3b0dadfb17" />

### SAWTOOTH WAVE

![WhatsApp Image 2025-09-19 at 12 19 05_d65e981b](https://github.com/user-attachments/assets/976bb336-fd7c-43e3-a953-f9e7c51683e0)

## Result

Thus, the **DAC was interfaced with 8086** and different **waveforms** were successfully generated.
