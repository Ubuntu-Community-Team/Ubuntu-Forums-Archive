---
title: "Gateway M305 question"
date: 2006-05-11
forum: Hardware &amp; Laptops
---

### Post by mcflynnthm on 2006-05-11
Alright, so I acquired this laptop, it's got an Intel i810 chipset inside, and I immediately put Dapper Drake Flight 7 on it. I feel this probably would have happened if I used Breezy, though; my screen's resolution won't go higher than 800x600, even though I *know* its native res is 1024x768.

I monkeyed with xorg.conf a bit, but to no avail. Anyone have suggestions, ideas? I can post the xorg.conf when I get it online, if that would help (no ethernet jack in this room; desktop is wireless).

I admit right now (though I'm sure you figured it out by now) that I'm pretty new to Linux. I've dabbled in it before, but I'm still learning. So I probably shouldn't have tried Dapper Drake :P

---

### Post by jwl007 on 2006-05-12
I also have a Gateway M305 that I used for college, and I tried throwing both Breezy and Warty on it, having the same resolution problem with the i810 chipset. 

I gave up after trying reconfiguring the xorg server and editing xorg.conf several times to no evail.

If anyone else has experience in getting this up and running, I would be greatly appreciative as well.:mrgreen:

---

### Post by mcflynnthm on 2006-05-12
Update:

So, I tried to add a Modeline (thankfully, I know someone who has the exact same laptop but running XP, so I could run PowerStrip), which *should* have worked fine. But, alas, not so much.

Here's what my Xorg.0.log told me:
(II) I810(0): Generic Monitor: Using hsync range of 28.00-51.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) I810(0): Not using mode "1024x768@60" (no mode of this name)
(II) I810(0): Not using mode "1024x768" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (800 -> 1024).
(--) I810(0): Virtual size is 800x600 (pitch 1024)
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(==) I810(0): DPI set to (75, 75)

And here's my monitor section of xorg.conf:
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
        Modeline        "1024x768@60" 65.578 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Thoughts?

---

### Post by jwl007 on 2006-05-12
This is somewhat off-topic, but are you by chance using a wireless NIC with the M305 laptop? More specifically, the Gateway WBM-120? I'm having troubles getting the wireless card (with supposedly PRISM2 based chipset) to work as well. 

I don't have my laptop with me at the moment, but hopefully we can collaborate and get this sucker of a laptop to work.

---

### Post by Monkey_See on 2006-05-14
Good day mcflynnthm,

I believe I had a similar problem to yours with my laptop (Although my chipset and gfx card is different to yours so your results may differ) when I first got it.  By default the "Modeline ..." line was in my xorg.conf, when I commented it out and edited my sceen section for my screen resolution it worked fine.

Below are the two sections of my xorg.conf if your interested.

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
#	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X600 (M24)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

```

Hope this helps,

M_See

---

### Post by mcflynnthm on 2006-05-14
No dice, but thanks for the help :-\

Also, has anyone tried videogen? I gave it a shot, but it didn't help.

---

### Post by jwl007 on 2006-05-15
If you google for Gateway M305 and xorg or Gateway M305 and linux, you'll find many posts on this.  I really do not want to believe this, but it looks like the M305 laptop and the i810 chipset will not work with Ubuntu's XServer (see: [http://www.leenooks.com/Video)](http://www.leenooks.com/Video)).  

There is, apparently a commercial XServer by Xi Graphics ([http://www.xig.com)](http://www.xig.com)), but it is a bit pricey.  The Desktop base price is $39.00 and the Laptop base price is $59.00.  There *are* demos available on their website for both products for testing purposes.

Lastly, it looks like the i810 is actually an alias for the Intel 852GM?  The i810 is actually the 'Desktop' driver and the 852GM is the 'Laptop' Driver.  (Correct me if I'm wrong).

Next, I'm going to scour the Internet for a open-source i810 or i852GM graphics driver, and see if that helps at all..  Otherwise I think this quest is going up the Linux creek without a paddle.

---

### Post by jwl007 on 2006-05-15
For a little humor out of this situation, here is an email I received yesterday from Gateway.  (I guess they don't get out of the Windows box too much ;))
> Email Tech 	
<emailtech@gateway.com> to me
	 More options	  May 14 (21 hours ago)
************************************************************************
Hello [Name witheld],

Thank you for using Gateway's Online E-mail Support.  Regarding your
concern wherein the system does not work with Linux's Xorg graphics
server, please be informed that based on the information you provided,
the issues you are experiencing are most likely caused by Linux's Xorg
graphics server.  When you purchased their product, you also purchased
support from the manufacturer.  I do not have the resources needed to
assist you with this product; therefore, your best option at this point
is to call the manufacturer, so they can help you troubleshoot this
issue.  They may have a simple resolution to this issue.

The answer to your question might be found in the FAQ section, tutorials
or a message board of their Web site.

Also, please be advised that Gateway has no available BIOS update to
make your video memory adjustable.

Another option is to call Answers By Gateway at (800) 229-1103 at a rate
of $2.95 per minute (billed to a credit card).  However, calling cards
are also available in 30 minute, 90 minute, or 1 Year unlimited usage.
For more information or to place your order, please contact a Gateway
Consultant at the address below.

For questions regarding billing issues with Answers by Gateway, please
call (877) 352-2716, if you used the 800 number above.  If you used the
900 number to contact Answers by Gateway, please call (701) 355-3910.

I sincerely hope one of the options above provides the information you
are requesting.


I have documented this correspondence in Service Request Number
2-2229967823 in our contact tracking database.  Please use this number
in the future if you need to contact us again regarding this issue.

Please reply to this message if you require further assistance with this
issue.  If your reply is received while I am out of the office, to
ensure a speedy resolution, your issue will be handled by one of my
colleagues.

Thank you.

[Name Witheld]
[Badge Witheld]
Online Customer Support Team
Gateway

---

### Post by mcflynnthm on 2006-05-15
haha yeah, clearly this is somewhat out of their tech support range. :P

I tried poking around via Google but found a lot of people with similar issues, but not a lot of answers :-\ I'll keep looking around and trying things out (short of buying that package; I'm not looking to throw a lot of money into this computer, since its essentially just a side-project).

---

