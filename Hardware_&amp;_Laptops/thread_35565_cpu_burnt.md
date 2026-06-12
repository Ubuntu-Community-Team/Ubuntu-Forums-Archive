---
title: "cpu burnt?"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by hellospencer on 2005-05-19
Hello,

this morning i powered on my machine and went away. Later on I came back and all I saw was a black screen. I resetted my machine with the same effect. After some thinking about what's wrong I came to the following:

I found my CPU fan not working, so after I went away the computer booted automatically into Ubuntu 5.04. After some time the CPU got so hot it burnt, so the screen went black and my retries came to the same result.

My question: Normally, if a certain temperature threshold is reached, the mainboard powers off the machine. Is it possible there is a connection between this process and the operation system?

I appreciate your help and comments.
-spencer

Some information on my machine: 
 * AMD 1800+ CPU
 * ASRock mainboard, SiS 963L 
 * It's not the video card or monitor, I tested those.
 * The monitor stays in standby mode during booting
 * The LEDs are working, for about one minute the harddisk LED is on, then goes off.

---

### Post by jasmuz on 2005-05-19
[QUOTE=hellospencer]Hello,

this morning i powered on my machine and went away. Later on I came back and all I saw was a black screen. I resetted my machine with the same effect. After some thinking about what's wrong I came to the following:

I found my CPU fan not working, so after I went away the computer booted automatically into Ubuntu 5.04. After some time the CPU got so hot it burnt, so the screen went black and my retries came to the same result.

My question: Normally, if a certain temperature threshold is reached, the mainboard powers off the machine. Is it possible there is a connection between this process and the operation system?

I appreciate your help and comments.
-spencer

Some information on my machine: 
 * AMD 1800+ CPU
 * ASRock mainboard, SiS 963L 
 * It's not the video card or monitor, I tested those.
 * The monitor stays in standby mode during booting
 * The LEDs are working, for about one minute the harddisk LED is on, then goes off.[/QUOTE]
 The only thing you can do from the OS is monitor the activity status of the fan, and the temperature with installed sensors.

I also have a ASRock mainboard with a AMD 2400+ CPU, when a configured temperature limit is reached it will shutdown. But by doing a reboot, maybe you overheated the Processor enough to damage it.

Did you verify the RAM memory?...if so, test that same processor in another machine before you decide to replace it.

---

### Post by penguinzrool on 2005-05-19
if the cpu's fried it's likely the computer would either do nothing at all, or give a load of beep codes at startup. as it seems to be doing something, check the ram and try resetting the bios by taking out the backup battery for 10 minutes or so.

---

### Post by hellospencer on 2005-05-20
Thanks for your responses.

Now I tested the RAM and it is ok. Since the computer doesn't beep at all I conclude the processor is ok too. So it must be the mainboard.

---

