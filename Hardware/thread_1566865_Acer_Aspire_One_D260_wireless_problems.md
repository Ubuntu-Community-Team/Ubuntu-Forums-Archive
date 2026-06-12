---
title: "Acer Aspire One D260 wireless problems"
date: 2010-09-02
forum: Hardware
---

### Post by tsp_2177 on 2010-09-02
Hi all, I am having a few problems trying to dual boot my acer aspire one D260, right now the OS is working perfectly except the wireless card isn't working, and i only have mono speaker tones. Can anyone help me fix these 2 problems? I have been using Ubuntu a few months now but still am very new to it. My other laptop had no problem picking up everything correctly so i was really hoping to get this working properly because Ubuntu is a really nice alternative to Win7 sometimes lol. The Version I'm trying to use is 10.04 and I am currently only running it on a USB drive if that makes a difference
Thanks for any help in advance!!!

---

### Post by tsp_2177 on 2010-09-05
Bump, any ideas guys? if i can't get it working i guess i'll just use windows 7 for it since it will be my primary school computer. Win7 runs OK but uses way more resources than even the regular ubuntu (non NBR) ram usage idle for Win7 (60%) where Ubuntu (Non NBR) is only like 20% :( Processor at idle is about the same but Ubuntu feels so much snappier even when it was running on a flash drive.
but a netbook is pretty much useless without wireless so there would be no reason to install it without the wireless working.

---

### Post by minimoke on 2010-09-07
A couple of questions:

- Is the WiFi LED on the front of the Netbook lit ie. Orange?

- Are any wireless networks listed when you click on the network/wireless icon in the notification area?

---

### Post by uranium-junkie on 2010-09-29
sorry about the late reply

Try this;

1. connect the laptop to the internet via a Ethernet cable
2. Go to hardware option on the preferences tab
3. install the propriety driver

If this doesn't work the card may have switched itself in to sleep mode to safe power. To manually override this (it will no switch off and will eat more power). Also I'm getting these steps from a third party and I don't understand how this is supposed to work... at all

1. Boot into windows
2. Go to control panel
3. go to hardware
4. click "device manager" in the hardware tab
4. Find the wireless card under the 'network adapters' tree
5. surf thought the properties until you find the power saving settings
6. turn to always on

---

