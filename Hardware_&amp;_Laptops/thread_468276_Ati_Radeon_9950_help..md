---
title: "Ati Radeon 9950 help."
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by Infinia on 2007-06-08
ATI RADEAON 9550! NOT 9950!! Sorry!
]
First of all I want to tell the problem that occurred when trying to install ubuntu. 
When choosing the country with the Magnifying glass on the Live CD, clicking anywhere on the map would cause the computer to "freeze up" . Sometimes I could move the mouse & sometimes I couldn't. (But I chose the county with the large list provided)

Now ubuntu is installed. I love it!
But when I have my restricted drivers on, the computer will 'randomly' restart or freeze up.
But without the drivers on my Cedega doesn't run Stacraft! We'll, it does in a way but the game looks all stretched and stuff. But when I take a screen shot, IT LOOKS PERFECTLY FINE IN THE SCREENSHOT! WTF!!!

So my brother told me it would be a good idea to post about my problems on this forum and also that its for sure the Video Card's problem. He also said to ask her for where to get Open Source drivers because they most likely work. Also my ZSNES works perfectly fine XD. So, where can I get these Open source ATI Drivers? Help me because I never want to go back to Windows!!

ps. i searched the forum for the drivers and I could'nt find any

infinia

---

### Post by angryfirelord on 2007-06-08
The open source ati driver is installed by default. Open a terminal and type **sudo gedit /etc/X11/xorg.conf**. Look for *Section "Device"* and under Driver, make sure it says "ati".

---

### Post by Infinia on 2007-06-09
It says :

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection


Please post what is is suppose to say, I HAVE just changed the vesa to saying ati... that's all I'm waiting on you!

---

### Post by angryfirelord on 2007-06-09
Yes, changing it to ati should have done the trick Try running a couple of 3d apps and see if that worked.

---

### Post by Infinia on 2007-06-09
So is that all I have to have changed or is there more to it?
I can have ZSNES roms working but when I go into full screen - starts to look like Starcraft does... 
Hmm... I hope you can help me solve this because I deleted Windows... So just got Ubuntu right now.

---

### Post by angryfirelord on 2007-06-09
That's normal if it looks grainy. Remember, these are games that were made in the early '90s. As long as the gameplay is smooth, you're ok.

---

### Post by Infinia on 2007-06-10
[IMG]http://img.photobucket.com/albums/v651/tristanbuke121/DSC00204.jpg[/IMG]
[IMG]http://img.photobucket.com/albums/v651/tristanbuke121/DSC00205.jpg[/IMG]
[IMG]http://img.photobucket.com/albums/v651/tristanbuke121/DSC00206.jpg[/IMG]
[IMG]http://img.photobucket.com/albums/v651/tristanbuke121/DSC00207.jpg[/IMG]
thats what happends.... SAME THING WITH ZSNES MAXIMIZED!!!!!!!!!!!!!!! ARGGGGGGGGG

---

### Post by Infinia on 2007-06-10
help?

---

### Post by angryfirelord on 2007-06-10
It's probably an issue with the open source ATI drivers and ZSNES. I'd recommend trying the fglrx drivers instead.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by Infinia on 2007-06-11
Omg Yes!!!! Fixed My Problems!~!!!!! Thank You!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by angryfirelord on 2007-06-14
You're welcome.  :)

Now, in case you don't know, what is the difference between the ati and fglrx driver?

The ati driver is completely open source, but in terms of speed, it only provides limited 3d acceleration and may not work with the newest ATI cards.

The fglrx driver is developed by ATI and is closed-source. It gives you more performance and supports more cards, but if there issues with it, they're not fixed as fast. Also, ATI sometimes doesn't keep up the newest xorg versions (however you shouldn't ave to worry about that in Ubuntu).

---

