# Advantage 2 - Upgrade Project

## Overview
This project breathes new life into the Kinesis Advantage 2, transforming it with comprehensive hardware and software upgrades that bring modern features while preserving the beloved ergonomic design.
#### Hardware Enhancements
This build utilizes the excellent PillzMod Pro as its foundation, enabling complete firmware replacement and native Bluetooth connectivity. To address the stock keyboard’s hollow acoustics, the interior has been lined with automotive sound dampening material for a more premium typing experience.
see [[Advantage 2 - Hardware Hacks]]
#### Software Stack
Powered by the Nice!Nano controller board and PillzMod Pro integration, this upgraded Advantage 2 runs ZMK firmware. This guide walks through the complete setup process, from initial configuration to advanced module customization.
see [[Advantage 2 - ZMK Remote repo]]
#### Future Upgrades
The only remaining stock components are the Cherry MX Brown switches. While there are no immediate plans for replacement, potential alternatives like Gazzew Boba U4T or Hakko Penguins could offer interesting tactile improvements. Suggestions welcome!

## Features supported
- [x] ZMK Studio 
- [x] Leader key
- [x] Home row mode
- [x] caps word
- [x] Helper.h
- [x] Tri State Layer
- [x] Macro
	- [x] with unicode support. 
###### Supported but not yet tested
- [ ] Combo

## Battery level Tweaks
the battery reporting is included so it can be visible in the os. 
bluetooth power, speed and timeour update too for better experience. 

**Deep Sleep is not support by the pcb as it is.**
in order to support it, the pcb needs to be modified so that col5 can be directly
connected to a GPIO pin. 

### 74HC595 Pinout

74HC595 pin diagram:

          ┌───────┐
     Q1 ──┤ 1  16 ├── VCC (3.3V) ←── Use this for 3.3V
     Q2 ──┤ 2  15 ├── Q0
     Q3 ──┤ 3  14 ├── SER (data in)
     Q4 ──┤ 4  13 ├── OE
     Q5 ──┤ 5  12 ├── RCLK (latch)    ←── Column 5 output
     Q6 ──┤ 6  11 ├── SRCLK (clock)
     Q7 ──┤ 7  10 ├── SRCLR (reset)
    GND ──┤ 8   9 ├── Q7' (serial out)
          └───────┘

  Power mod:
  ┌──────────┬───────────────┬─────────────────────────────────────────┐
  │   What   │      Pin      │               Description               │
  ├──────────┼───────────────┼─────────────────────────────────────────┤
  │ Column 5 │ Pin 5 (Q5/QF) │ Connect one end of 10kΩ resistor here   │
  ├──────────┼───────────────┼─────────────────────────────────────────┤
  │ 3.3V     │ Pin 16 (VCC)  │ Connect other end of 10kΩ resistor here │
  └──────────┴───────────────┴─────────────────────────────────────────┘

## Layout

### layers
DEFAULT 0
LOWER   1
RAISE   2
FN      3
SYSTEM  4

### Keymap Summary Table 

| Action             | Key       | Layer   | Shortcut           |     |     |
| ------------------ | --------- | ------- | ------------------ | --- | --- |
| Grave              | Grave     | Default |                    |     |     |
| Desk Left          | LCtrl     | Default | &kp LG(PG_UP)      |     |     |
| Desk Right         | RCtrl     | Default | &kp LG(PG_DN)      |     |     |
| Folder Home        | F8        | Default | &kp LG(SPACE)      |     |     |
| Desk 1             | F1        | Default | &kp LA(LG(N1))     |     |     |
| Desk 2             | F2        | Default | &kp LA(LG(N2))     |     |     |
| Desk 3             | F3        | Default | &kp LA(LG(N3))     |     |     |
| Desk 4             | F4        | Default | &kp LA(LG(N4))     |     |     |
| FN layer           | keypad    | Default |                    |     |     |
| Sys Layer          | prgm      | Default |                    |     |     |
| Lower Layer        | esc       | Default |                    |     |     |
| Raise Layer        | enter     | Default |                    |     |     |
| delete             | T         | Lower   | &kp DEL            |     |     |
| select all         | A         | Lower   | &kp LC(A)          |     |     |
| shift + tab        | S         | Lower   | &kp LS(TAB)        |     |     |
| super              | D         | Lower   | &kp LGUI           |     |     |
| tab                | F         | Lower   | &kp TAB            |     |     |
| undo               | Z         | Lower   | &kp LC(Z)          |     |     |
| cut                | X         | Lower   | &kp LC(X)          |     |     |
| copy               | C         | Lower   | &kp LC(C)          |     |     |
| paste              | V         | Lower   | &kp LC(V)          |     |     |
| --                 | B         | Lower   | &kp LC(B)          |     |     |
| Ghostly            | F9        | Lower   | &kp LS(LC(LG(N1))) |     |     |
| Brave              | F10       | Lower   | &kp LS(LC(LG(N2))) |     |     |
| Obsidian           | F11       | Lower   | &kp LS(LC(LG(N3))) |     |     |
| 1Password          | F12       | Lower   | &kp LS(LC(LG(N4))) |     |     |
| LEFT               | h         | Lower   | &kp LEFT           |     |     |
| DOWN               | j         | Lower   | &kp DOWN           |     |     |
| UP                 | k         | Lower   | &kp UP             |     |     |
| RIGHT              | l         | Lower   | &kp RIGHT          |     |     |
| Move win to ws 1   | F1        | Raise   | &kp LG(LS(N1))     |     |     |
| Move win to ws 2   | F2        | Raise   | &kp LG(LS(N2))     |     |     |
| Move win to ws 3   | F3        | Raise   | &kp LG(LS(N3))     |     |     |
| Move win to ws 4   | F3        | Raise   | &kp LG(LS(N4))     |     |     |
| Gui +              | +         | Raise   | &kp LC(EQUAL)      |     |     |
| Gui -              | -         | Raise   | &kp LC(MINUS)      |     |     |
| Hide Win           | U         | Raise   | &kp LG(H)          |     |     |
| set win Left       | H         | Raise   | &kp LG(LEFT)       |     |     |
| Win reduce         | J         | Raise   | &kp LG(DOWN)       |     |     |
| Win Full Screen    | K         | Raise   | &kp LG(UP)         |     |     |
| Set Win Right      | L         | Raise   | &kp LG(RIGHT)      |     |     |
| (                  | E         | Raise   | &kp LPAR           |     |     |
| )                  | R         | Raise   | &kp RPAR           |     |     |
| [                  | S         | Raise   | kp LBKT            |     |     |
| ]                  | D         | Raise   | &kp RBKT           |     |     |
| {                  | C         | Raise   | &kp LBRC           |     |     |
| }                  | V         | Raise   | &kp RBRC           |     |     |
| Default adv2 F row |           | FN      |                    |     |     |
| unlock zmk studio  | esc       | SYS     | &studio_unlock     |     |     |
| bt 1               | f1        | SYS     | &bt BT_SEL 0       |     |     |
| bt2                | f2        | SYS     | &bt BT_SEL 1       |     |     |
| bt3                | f3        | SYS     | &bt BT_SEL 2       |     |     |
| bt4                | r4        | SYS     | &bt BT_SEL 3       |     |     |
| bt clear           | f8        | SYS     | &bt BT_CLR         |     |     |
| boot loader mode   | shift     | SYS     | &bootloader        |     |     |
| keyboard reset     | thumb esc | SYS     | &reset             |     |     |


## Credits
https://github.com/dcpedit/pillzmod

https://github.com/masters3d/zmk-config-pillzmod-nicenano

https://github.com/urob/zmk-leader-key

https://github.com/urob/zmk-helpers

