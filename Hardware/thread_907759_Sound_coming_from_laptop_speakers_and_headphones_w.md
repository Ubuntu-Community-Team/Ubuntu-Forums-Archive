---
title: "Sound coming from laptop speakers and headphones when plugged in"
date: 2008-09-01
forum: Hardware
---

### Post by Raspe28 on 2008-09-01
I'm running the latest version of Ubuntu and haven't had any issues until I tried to listen to music through my headphones only.  I've tried muting the laptop speakers but when I do that it just mutes both speakers and headphones.  It seems to have a problem with telling the difference between the two.  What I do to one has the same effect on the other.  

I'm running an ATI sound chip/card in my laptop.  I know there is a terminal command that will give you the exact card/chip in my laptop but I don't know what it is and my bandwith is pretty limited while at sea so it's hard for me to search for anything right now.  Most of the previous posts I've found dealing with this problem have been with Intel based chips/cards and since I'm running an AMD/ATI combination, I'm not sure if the advice given in those posts will work for me.  If anyone can help me solve this I would greatly appreciate it.  Please keep in mind that I'm brand new to Linux and I'm not to familiar with the terminal commands and how to do certain things in the OS.  Thanks in advance.

---

### Post by Psychoscorpic on 2008-09-02
I'm finding the same thing (Also ATI audio chip).

(See posts on getting audio to work on laptops for the "module" setting)

Setting module to "lenovo" (my machine is actually a Sahara, but this setting works) then I get audio from the speakers, but not the headphones.

If I set module to "auto" then I get audio from the headphone socket, but not the speakers.

---

### Post by Raspe28 on 2008-09-02
Thanks for the info but I'm not sure where the "module" setting is.

Edit:  I found a guide and I got this information in modules.

I typed in cat /proc/asound/modules and it came up with this
0 snd_hda_intel
1 snd_hda_intel

I'm guessing it's thinking I have intel chipsets but I have an ATI sound device.  Is there any way to change this?

---

### Post by Psychoscorpic on 2008-09-03
Hi Raspe28

No need to change them - those are hardware.

Do the following:

```
sudo gedit /etc/modprobe.d/alsa-base
```

Right at the end of the page, add the following line:

```
options snd-hda-intel model=hp
```

Note: You may need to try different models or settings for your specific chipset etc.
Use
```
cat /proc/asound/card0/codec#* | grep Codec
```
(Look for your chipset (or the closest match) at [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt")

A few you could try instead of "hp" are:
lenovo ; 3stack ; dallas ; auto
Reboot after saving, and see whether you are getting sound from both the speakers and the headphone socket.

Note: Your actual machine may be listed, or not. My machine is a Sahara, with an ATI audio chip, but using the "hp" model setting does the trick for me.

---

### Post by Raspe28 on 2008-09-03
I'll give it a try tonight and post the results.  Thanks for all of your help.

---

### Post by Xochipilli on 2008-09-03
Hey,

I got the same problem here. I started working in Ubuntu a month ago, so I'm a total noob in this linux thing. I was surprised that most things worked properly from the first time. But this headphone issue is something that won't work correctly. I always work on my laptop with headphones on so this problem is really one of the only things that keeps me from using Linux.

So my problem is exactly the same, I hear sound from the headphones and the laptop speakers, but it seems impossible to mute the laptop speakers without muting the headphone. I also tried the above, but It would be possible if I did something wrong, because these terminal commands are still like riddles to me.

My laptop is a Fujitsu-Siemens Amilo PA2510

the "cat /proc/asound/card0/codec#* | grep Codec" code says this:
```

Codec: Motorola Si3054
Codec: Realtek ALC883

```

---

### Post by Raspe28 on 2008-09-03
Well I tried typing in those commands and the alsa-base is completely empty.  I'm guessing that there's something I need to download so if you could provide a link to it that'd be great.  I dont have an internet connection for my laptop right now so those terminal commands to auto download stuff won't work.

---

### Post by mkrahmeh on 2008-09-03
hope this link helps
[http://packages.debian.org/lenny/all/alsa-base/download]("http://packages.debian.org/lenny/all/alsa-base/download")

you will find a list of locations from which you can download the alsa-base configuration files
but pay attention that the alsa-base will be downloaded with a .deb extension, when you copy this file to your laptop from elsewhere you need to check the method on how to install .deb packages to your system.
if you could connect your laptop to the internet, things would be much easier for you, such that you can instantly type 
```
sudo apt-get install alsa-base
```
or use the package manager (like synoptic) to do this stuff for you..
good luck

---

### Post by Psychoscorpic on 2008-09-04
Hi Raspe28

alsa-base cannot be empty - it is a main configuration file.
However, if you type the command incorrectly (not pointing it to the existing file, using caps, or misspelling it), you are actually telling it to create the file, and open it in gedit - which is why you're seeing a blank file.

Make sure you're typing it correctly.

(You can verify the existence of the file by browsing there and opening it. You won't be able to save any edits this way, since you won't be opening it as super-user (sudo = "super user: do [this command]"))

Waiting to see how it goes.

---

### Post by Xochipilli on 2008-09-04
I tried the following, and I still got no change:

```
sudo apt-get install alsa-base
```
-> alsa-base is already the newest version.
I think I read about updating the alsa-base before I read this topic, So I probably already tried it.

```
sudo gedit /etc/modprobe.d/alsa-base
```
Added ```
options snd-hda-intel model=fujitsu
``` after the last line saying: ```
options snd-cmipci mpu_port=0x330 fm_port=0x388
```
I got no change from this, I also tried the following instead of "fujitsu": "hp, auto, laptop-micsense, lenovo, 3stack, dallas". I also got no change from them.

---

### Post by Psychoscorpic on 2008-09-04
Hi Xochipilli

Seems your setup is being a tad uncooperative! :)

According to your chipset, you should have success with one of the following (use the info on the right to match your hardware):
```
**ALC883**/888
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  3stack-6ch    3-jack 6-channel
	  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
	  6stack-dig-demo  6-jack digital for Intel demo board
	  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
	  acer-aspire	Acer Aspire 9810
	  medion	Medion Laptops
	  medion-md2	Medion MD2
	  targa-dig	Targa/MSI
	  targa-2ch-dig	Targs/MSI with 2-channel
	  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
	  lenovo-101e	Lenovo 101E
	  lenovo-nb0763	Lenovo NB0763
	  lenovo-ms7195-dig Lenovo MS7195
	  haier-w66	Haier W66
	  6stack-hp	HP machines with 6stack (Nettle boards)
	  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
	  6stack-dell	Dell machines with 6stack (Inspiron 530)
	  mitac		Mitac 8252D
	  auto		auto-config reading BIOS (default)

```

That should keep you out of mischief for a while!
I didn't see anything specific for the Motorola, but hopefully these will work.

---

### Post by Raspe28 on 2008-09-04
Ok I managed to get the alsa-base package downloaded and installed so now something comes up with I type the previous command you listed.  I added the code at the very bottom of the page and tried all of the variants you listed but none worked.  I went to the previous page but didn't see my chipset listed.  I am running an ALC888 I believe and I couldn't find anything close enough on the list to try.  Any ideas?

Edit:  My connection is slow so I didn't see the previous post.  I'll give those a try since it's for the ALC888.  Thanks.

---

### Post by Xochipilli on 2008-09-08
I fixed the problem on my laptop.
I found the solution here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/114053/comments/41]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/114053/comments/41")

Thanks everybody for helping.

*EDIT*
Ok, my problem has been fixed, but a new problem arose. Now, my laptop speakers won't play any sound. This is less trouble for me, but if anyone knows how to fix it without side effects, please let me know.

---

### Post by mid_life_crisis on 2010-07-21
I get this.

Codec: Conexant ID 5067

Any suggestions as to what I need to add to get the speakers to turn off?

---

