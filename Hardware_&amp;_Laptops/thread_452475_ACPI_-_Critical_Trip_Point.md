---
title: "ACPI - Critical Trip Point"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by irv on 2007-05-23
I thought this would be a good place to post this problem I had and found a solution too.
This happen to me yesterday. I was doing some scanning and converting to text using OCR software. (GIMP Image Editor & gocr to convert). gocr creates a text file and stores the OCR data into it. After the conversion I checked the properties of the file and my laptop made a popping sound and when black. I don't believe I have ever had a hard crash like this before.
Well, I have a duel boot system. Ubuntu Feisty Fawn 7.04 and WinXP. When I tried to restart in either OS the laptop would just shut down. The next step I tried was to boot in Ubuntu recovery mode and I got a message “ACPI – Critical Trip Point” and then it told me that it had reached a critical temp of 105C. The fix for this problem was to take the cover off the bottom of my laptop and remove the fan from the CPU, clean it and blow out the dust from the fan itself. Then I removed the small battery from the mother board and the laptop battery. Also the laptop was unplugged when I was doing all this. After re-installing the fan on the CPU and putting the batteries back in I started the laptop back up and everything worked again.
I believe the problem was I overloaded the CPU because I had four workspaces  going with a lot of applications running. I believe it was (the straw that broke the camels back).
I hope this information will help someone who might run into this same problem.

---

### Post by Adnarim on 2007-05-25
I have the same problem since Feisty :( But I don't want to open my laptop because I'm loosing the garantee then.. Any other possibility to small the temperature?

maybe dm_crypt is too heavy for laptops?

---

