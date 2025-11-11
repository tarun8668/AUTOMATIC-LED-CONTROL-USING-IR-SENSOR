# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/cb534d8a-c1ba-4c17-886d-352090c5e78e" />

2. Click **File → New STM32 Project**.
   <img width="1833" height="1065" alt="image" src="https://github.com/user-attachments/assets/b02458cf-2e23-4602-b733-4f3ac2f0b977" />


3. Select the **target microcontroller** or board and click **Next**.
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/ebb9a4b1-7967-4603-a2cb-a1bd1fabb7b8" />

4. Name the project.
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/4c814977-e1ab-4cc1-9e02-18de3e5a0b87" />


5. The corresponding `.ioc` file will be generated automatically.
  <img width="1917" height="1077" alt="image" src="https://github.com/user-attachments/assets/43989f55-2a9a-4d36-a001-74896fa350e3" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/ec6d53fe-3781-4745-ba1e-0774692d44d2" />
	<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/0f05b90d-7274-469f-b3b6-149c3f76b138" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/8f244250-8e72-493b-a20c-e04e973a3986" />

8. Edit the generated main program as required.
 

9. Click **Project → Build All**.
    <img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/fb6b08c9-27f9-44d8-86ef-fec3e63f430f" />


10. Link the **HEX file** using the post-build process.
    <img width="1911" height="1078" alt="image" src="https://github.com/user-attachments/assets/f534c1b8-1d24-4f01-aa94-e788066546c0" />

11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/4f061269-6e3a-42ba-8303-a14261126eca" />



12. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
![IMG-20251030-WA0011 1](https://github.com/user-attachments/assets/66a426de-f676-422f-af78-9fc1f28ee4ae)

CASE 2: LED OFF
![IMG-20251029-WA0021 1](https://github.com/user-attachments/assets/cb900a9d-4921-47ba-8876-30c23a740d4d)
---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




