---
title: "Best config for H100i v2 on Linux"
date: 2017-07-03
forum: Hardware
---

### Post by eera5607 on 2017-07-03
Hi everyone. I've been reading a lot about H100i v2 and Linux compatibility issues.I know that in some cases the pump isn't running at an adequate speed (some people say the default speed is the slower possible). Since us, the Linux users, can't install Corsair Link the configuration is limited. I understand that in some cases the motherboard model can help to mitigate some issues and this is why I created this thread, to ask what would you recommend in the cases I will present. I decided that since the Linux support is limited I won't use at the moment some [scripts or implementations]("https://tekwiki.beylix.co.uk/index.php/Corsair_H100i_Linux_howto") published on different forums and therefor I won't use the Corsair Link Cable. Do you know an alternative to those scripts but compatible with the v2? I post this here because here is more possible that I can find other Ubuntu users with the same issue. 


Option 1: **Asus Maximus IX Code **and similar motherboards have a set of 7 - 9 headers to connect all thing related to cooling. See image below. 
[IMG]http://i.imgur.com/J0V6DbX.jpg[/IMG]

The first option is follow the user's manual and connect the pump directly to the CPU_FAN (Q-Fan Controlled) header and the fans to the two connectors coming off the pump. In this case I think the pump speed will depend on the CPU temperature and fans will run at a constant speed (determined by what? default speed?) Is that correct? Following the instructions [here]("http://&quot;http://forum.corsair.com/forums/showthread.php?t=168801") would configure full voltage from the BIOS to CPU_FAN.


Option 2: Taking into consideration the information in the image below:
[IMG]http://i.imgur.com/vfz5X2D.jpg[/IMG]
What about connecting the pump to the AIO_PUMP header and the fans directly to the two connectors coming off the pump? Since the default speed in that header is "Full speed" will the pump run always at max speed and the fans at the same default speed of option 1? In that case we will probable get a boot warning, depends on the motherboard and BIOS (no CPU_FAN connected). 


Option 3: What about connecting the pump to AIO_PUMP and the two fans directly to the CPU_FAN and CPU_OPT? In that case we won't get a boot warning and the pump will work at full speed and the fans will run at variable speeds depending on the CPU temp. Is that correct? Remember that CHA_FAN's and CPU_FAN and OPT headers can be configure from the BIOS.


What other ideas do you have? Maybe connect the the pump to a CHA_FAN header? 
What is the best option? Thank you very much for your help. 


Sorry for the grammar and other mistakes, English isn't my native language.

---

### Post by gordintoronto on 2017-07-05
I think most people would need more context for your question. I think the H100i is for water-cooling your CPU?

---

### Post by eera5607 on 2017-07-06
Yes sorry. It is an AIO.

---

