---
title: "ATI HD 3600 Issues"
date: 2010-11-14
forum: Hardware
---

### Post by Toxcity on 2010-11-14
Evening all, 

Still having issues with my ATI card. What I have done is reinstall the drivers and all went really well. 

But the driver can't seem to see my card. 

I used this: 

```
lspci -nn | grep VGA
```

And I get this as a result:

```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3600 Series [1002:9598]

```

Now, I know for a fact my card is not a mobile chip. It's the normal desktop card. Any ideas? I have no idea how any desktop trickery is working. :) 

Thanks in advance!

---

### Post by Toxcity on 2010-11-15
Bump :P

---

### Post by mastablasta on 2010-11-15
don't bump a thread unless it's over two days old.
 
How did you install the drivers? 
 
What do you mean driver does not see your card?

---

### Post by gordintoronto on 2010-11-15
There's good reason for putting a mobility chip in a desktop expansion card: lower power, therefore less cooling required. I would believe what my computer tells me in this case.

Unless the card has a honkin' great heat sink and fan...

---

### Post by Toxcity on 2010-11-15
Sorry for bumping.

I installed them according to the guide on [**this**]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") web page.

The reason I didn't use Jocky is because it seems to have glitched up since it says I am using FireGL drivers but I have a HD3600 normal GPU. 

I'm not new to computing just new(ish) to Linux. All my machines are built by me so I know exactly what is in them. To add more, I have the box for the GPU and Windows 7 sees it as a HD3600.

---

### Post by gordintoronto on 2010-11-15
You haven't said why you think "But the driver can't seem to see my card."

What video card is it?

---

### Post by sunnynice on 2010-11-15
> **gordintoronto said:**
> You haven't said why you think "But the driver can't seem to see my card."
 
What video card is it?
 Yup, video card is an important issue.

---

### Post by jamesjony2 on 2010-11-15
ATI Radeon HD 3600 AGP graphics card, but when I install the drivers for it, it shows that I have a standard VGA adapter.Quitting and then reload the game seems to fix it, but if I run into another issue 'm wondering.

---

### Post by Toxcity on 2010-11-16
The card is a ATI Radeon HD 3600 PCI-E. I don't seem to have an xorg.conf file either.. :(

---

### Post by gordintoronto on 2010-11-16
Sorry, I'm interested in the brand and model, not just what chip it has.

Tox, it's normal to have no xorg.conf, but you can create one.

---

### Post by Toxcity on 2010-11-17
Okay, I gave up. Reinstalled with a check list of things to do and install. 
I have the normal ATI drivers now installed, what is really bothering me know is the lack of performance. It seems that my card operates better with ATIs driver. 

Docky is laggy, compiz is laggy. Nothing seems smooth and it can't detect the monitor properly. Bloody ATI...

---

