---
title: "Hard drive boots from external usb but not from internal drive"
date: 2011-03-30
forum: Hardware
---

### Post by kcbrown on 2011-03-30
After doing some partitioning on my hard drive, using gparted (created an NTFS partition on my /home file), I got a message when I restarted my computer that "no bootable devices--strike F1..." It seems like my laptop (dell latitude e6400) stopped recognizing my hard drive, call it A (seagate momentus 320gb SATA). 

I placed another working hard drive, call it B (Hitachi 80gb travelstar SATA), in the internal hd bay of the laptop and it was indeed recognized. So I thought hd A stopped working. While B was in the internal hd bay in the latop, I attached hd A via a usb enclosure I had. I was able to still read and write data from hd A as an external usb hard drive. 

I was then able to install ubuntu 9.10 on hd A, the apparently broken one, via the usb connection using a live CD. Then I tried booting from the usb drive, which is attached to hd A. It worked! However, when I try to attach hd A internally to the hd bay of the laptop, the BIOS will not recognize the hd. 

SUMMARY: HD with ubuntu 9.10 will boot via external usb connection, but when I place the hd internally into the laptop, BIOS will not recognize the drive (I get "no bootable devices..."

How can the laptop boot from the hd while its connected via usb, but not boot if the hard drive is directly connected to the computer? The internal hd laptop bay works fine with another hd just fine so it cannot be the computer?

---

### Post by Lateralis on 2011-03-30
I'm going to ask two very stupid questions, which I think I already know the answer to, just as a sanity check. 

Firstly: did you try installing Ubuntu onto drive B and booting from that when it was in the internal drive bay?  Or did it already have an OS on it?  If yes, were you successful in booting?  

Secondly: Have you changed anything in the BIOS which would stop it from looking at internally connected hard drives for an OS?  Have you double checked the BIOS anyway as a sanity check?

---

### Post by oldfred on 2011-03-30
With both drives plugged in run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

And tell us which drive is which.

---

