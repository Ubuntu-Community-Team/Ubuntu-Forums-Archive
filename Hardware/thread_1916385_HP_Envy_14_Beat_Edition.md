---
title: "HP Envy 14 Beat Edition"
date: 2012-01-27
forum: Hardware
---

### Post by bbeaupre on 2012-01-27
Hello Everyone,

I purchase a HP Envy 14 inch Beat Edition, this computer as a quad core i5, 6gig or memory and a 750gig 7200RPM HD, it also as a red back lit keyboard, wireless and bluetooth built in.

I tried to install Ubuntu 64 bit version 11.10, most of all the driver are working out of the box exept for the video card, the sound card and also the CPU fan.

Here is a brief descriptions of the problems:

1- The CPU fan seems to be draining the battery since its running full speed all the time, it could be a sensor driver not working properly.

2- The video card does work, but evertime you boot the computer, the screen is turn off, you have to increase the brightness to have the screen turn on, pretty weird.

3- The sound card does the same thing as the screen in some ways, the sound off/on button as a red light in it to indicate that the sound is off, when you boot, the sound light indicate the sound is off but its actually working, when you press on it, it turn off the sound...

I'm using and old and slow Toshiba right now that is working fine with Ubuntu 11.10 but I would like to be able to get Ubuntu to work properly on it, mind you the screen and sound are not that bad, but the CPU fan sound like a 747 in my living room and it will only gives me about 60 minutes of battery instead of the 4.5 hours I used to get with Windows or Wincrap as I call it.

Thanks in advance for any help or tips you could give me!
Cheers

---

### Post by wolfen69 on 2012-01-27
How old is this computer? The reason I ask is because "fresh off the line" hardware needs time before it can be properly supported.

---

### Post by bbeaupre on 2012-01-28
> **wolfen69 said:**
> How old is this computer? The reason I ask is because "fresh off the line" hardware needs time before it can be properly supported.
Hi there,

Thanks for the reply, the first edition came out in 2009, I think mine came out in fall 2010 with the i5 processor but I'm not to sure.

I did do a lot of reading about these problems with this exact laptop model, there is even a guy who as a web page the is trying to fix these problem.

I'm not knew in the computer world but I am new to Linux (Ubuntu), I love this Distro compare to all the other one, its my favorite, I'm thinking about selling this computer which I bought just before christmas to get something that will work properly with Ubuntu but, again, after looking left and right, I'm not sure there is one laptop I would have to buy.

If I could fix the fan problem that drain the battery it would not be so bad, I chose this laptop because its an amazing machine and in my case I was looking for a laptop that you can add a extended or a second battery to extend the running time to be able to work with it all day without carying a charger, this is one of them.

Thanks for your help!

---

### Post by Dlambert on 2012-01-28
Does the "additional drivers" yield any results?

---

### Post by bbeaupre on 2012-01-29
> **Dlambert said:**
> Does the "additional drivers" yield any results?

Actually, according to the system there is no 'additional driver' to install, which is pretty weird, I did some more test today with Ubuntu 10.10 LTS and its doing the same thing...

---

### Post by Mark Phelps on 2012-01-29
The HP Envy's have switchable graphics -- which doesn't work well with Linux.

More info at the link:

[http://www.phoronix.com/scan.php?page=news_item&px=MTAwOTA]("http://www.phoronix.com/scan.php?page=news_item&px=MTAwOTA")

---

### Post by bbeaupre on 2012-01-30
> **Mark Phelps said:**
> The HP Envy's have switchable graphics -- which doesn't work well with Linux.

More info at the link:

[http://www.phoronix.com/scan.php?page=news_item&px=MTAwOTA](http://www.phoronix.com/scan.php?page=news_item&px=MTAwOTA)

Thanks Mark,

As they say, even bad news is good news, I knew about the graphic card and I also did try with the FIX option in the BIOS but its still a bitch. I'll just have wait and for now use Win7 on it...

Good reading by the way, Cheers !

---

### Post by onefthemany on 2012-05-24
> **bbeaupre said:**
> Thanks Mark,

As they say, even bad news is good news, I knew about the graphic card and I also did try with the FIX option in the BIOS but its still a bitch. I'll just have wait and for now use Win7 on it...

Good reading by the way, Cheers !


I also have an HP Envy 14 and my switchable graphics work just fine (Ubuntu 12.04) and I don't even have to reboot for the change to take effect..

Check this thread where I have scripts that run with gxmessage and screen shots showing the step process:

[http://ubuntuforums.org/showthread.php?p=11965089#post11965089](http://ubuntuforums.org/showthread.php?p=11965089#post11965089)

I still have to work out how to get the script to run automatically when the laptop is on battery and also retain the command so you don't have to run it everytime you reboot.

Good Luck

---

### Post by His Eminence on 2012-07-04
I can't get Ubuntu 12 to boot on an HP Envy 14. The installation starts but then I just get a black screen. Any suggestions? I was using a KUbuntu image put on an USB stick, I also tried to install it within Windows (wabi) but got the same result - black screen.

---

### Post by bill_mchale on 2012-08-06
> **His Eminence said:**
> I can't get Ubuntu 12 to boot on an HP Envy 14. The installation starts but then I just get a black screen. Any suggestions? I was using a KUbuntu image put on an USB stick, I also tried to install it within Windows (wabi) but got the same result - black screen.

Have you tried a different image?  Does it beat off the USB stick?  

--
Bill

---

### Post by Starcruiser1229 on 2012-08-18
I had the exact same problem (blank screen on boot) and it turned out that it was booting fine but for whatever reason it turned the backlight off on boot. Try using the keyboard buttons to increase the backlight, and see if that fixes the problem. If it does, a more permanent solution is to edit /etc/default/grub and change the line which reads:
[COLOR=#0000ff]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[COLOR=Black]to 
[/COLOR][/COLOR][COLOR=#0000ff]GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux acpi_backlight=vendor splash"
[COLOR=Black]And then do [COLOR=Blue]sudo update-grub
[COLOR=Black]and reboot - it should come up with the correct backlight setting.

Hope this helps!
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by His Eminence on 2012-09-29
Starcruiser1229, thanks for this! You solved my problem and now, after waiting almost a year I'm happily using Kubuntu on my laptop. And I feel stupid for not trying the brightness buttons before...

---

