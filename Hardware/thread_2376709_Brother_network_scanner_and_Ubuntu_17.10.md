---
title: "Brother network scanner and Ubuntu 17.10"
date: 2017-11-05
forum: Hardware
---

### Post by kurt18947 on 2017-11-05
I'm having an issue getting Ubuntu 17.10 to recognize my Brother MFC-6490CW scanner. It's connected via a network with static I.P. address 192.168.1.90. The scanner function is working as expected in Ubuntu-Gnome 16.04. The machine prints as expected in 17.10. I've done the usual install steps for the scanner:

[LIST]
[*]Ran the script which installed the appropriate .deb files
[*]Copied the files from /usr/lib64  to /usr/lib
[*]Ran the command to register the scanner with sane.
[/LIST]

Here are the contents of /usr/local/brother/sane/brsanenetdevice3:

```
DEVICE=brotherscanner , "MFC-6490CW" , 0x4f9:0x1f3 , IP-ADDRESS=192.168.1.90
```

I take that to mean that Sane knows about the Brother scanner. It just isn't found by SimpleScan or Gscan2pdf. Has anyone run into similar and found a solution? Brother does provide email support for Linux so I will see if they have any insights in a few days.

---

### Post by william.hua on 2017-11-05
See if this video helps.
[https://www.youtube.com/watch?v=c3oT2iT4pIY](https://www.youtube.com/watch?v=c3oT2iT4pIY)

---

### Post by kurt18947 on 2017-11-05
> **william.hua said:**
> See if this video helps.
[https://www.youtube.com/watch?v=c3oT2iT4pIY](https://www.youtube.com/watch?v=c3oT2iT4pIY)

Hi William

Thanks for your reply. The video seems correct and I performed those steps. Everything seems okay until I open Simple Scan and click 'scan'. Then it says no device found. I'm hoping to hear something from Brother support or from someone here who has had the same experience and was able to solve the mystery. 16.04 works very well but perhaps something in SANE has changed. I'm not knowledgeable enough about SANE to ferret out the issue.

---

### Post by pdc on 2017-11-05
curious thread on the OpenSuse forum [https://forums.opensuse.org/showthread.php/527893-Unable-to-communicate-with-scanner-part-of-printer-scanner/page2](https://forums.opensuse.org/showthread.php/527893-Unable-to-communicate-with-scanner-part-of-printer-scanner/page2)

the solution was for the person to be admitted to the lp group ..... when I check, I see I am in the lpadmin group ........ but not lp (I am NOT running a Brother scanner I should make clear ........)

I only offer this up as some of these things seem "in the dark" and one has to try various issues ........... 

........ to refresh my memory, from here   [https://askubuntu.com/questions/79565/how-to-add-existing-user-to-an-existing-group](https://askubuntu.com/questions/79565/how-to-add-existing-user-to-an-existing-group)   it would seem the command would be something like ```
sudo usermod -a -G lp username
```; others may well take exception to this command

---

### Post by kurt18947 on 2017-11-07
Thanks PDC. I'm not able to try that now but will do so this weekend.

---

### Post by pavelone on 2017-11-07
I have the same problem with network Brother MFC-7840W and Ubuntu 17.10.

---

### Post by pdc on 2017-11-08
so there are several things folks seem to need to do; with a Brother scanner          [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on)

1) [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107) ....... even though it is networked you seem to need libusb so ```
sudo apt install libusb-0.1-4
```

2) copy some files as per here [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101) so the 7840W is brscan3 so  ........```
sudo cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
sudo cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
sudo cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
sudo cp /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
sudo cp /usr/lib64/libbrscandec3.so /usr/lib
sudo cp /usr/lib64/libbrscandec3.so.1 /usr/lib
```

3) check formatting as per here [http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on)

......... kurt has done all of this but no joy seemingly

---

### Post by kurt18947 on 2017-11-16
To update this thread. Still no joy on the Brother scanner. I did email Brother - they offer limited Linux support. Their suggestion was to try scanning from a SUDO account. That didn't help and I haven't heard back. I did take the time to install a second scanner, Samsung SL-M2870 which has installed without a problem on 16.04 and earlier. I have the Samsung Linux drivers and same result. The script reports success installing but the scanner is not found.  Sane-find-scanner doesn't find anything. I wonder if SANE needs an update or something. I may try a USB connection to see if the problem lies in the network connection.

---

### Post by kurt18947 on 2017-11-19
Another update: VueScan does find both scanners in 17.10. I want to be able to use gscan2pdf though.

---

### Post by kurt18947 on 2018-04-03
The problem turns out to be similar to Brother printers; the install routine places files in /usr/lib64 when they should be in /usr/lib. The solution is different for 64 bit and 32 bit users.

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00108](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00108)

```
**I cannot find the Brother Machine.** 


[LIST]
[*]**Related Distribution : Ubuntu, LinuxMint, Debian** 
[*]**Related Scanner Driver : brscan, brscan2, brscan3** 
[/LIST]


 Check if the following directory exist.

    **For 64bit Users:**
/usr/lib/x86_64-linux-gnu/sane
&#12288; 
    **For 32bit Users:**
/usr/lib/i386-linux-gnu/sane


 Type the following command if the above directory exist.

    **For 64bit Users:**
    **Command : sudo cp  /usr/lib64/sane/libsane-brother*   /usr/lib/x86_64-linux-gnu/sane**

     **For 32bit Users:**
    **Command : sudo cp  /usr/lib/sane/libsane-brother*     /usr/lib/i386-linux-gnu/sane**


```

I feel so much better now :D. 18.04 seems to be coming along very nicely but I really need the Brother scanner to work before I can upgrade. I'll still wait a few weeks after the release of 18.04 for the dust to settle but now my hardware issue seems solved.

---

### Post by fredaime on 2018-06-26
Great solution !! works on 18.04

So you can go for it...

Thanks that saved me ;)

---

### Post by PEM59 on 2018-12-27
I have a similar problem on Ubuntu 18.04.  I am using a network.  
I have a Brother MFC-7620DN scanner (B&W Laser All in one) that I have been using for some time in sane.  It is a brscan4 scanner. 
I just bought a new color inkjet MFC-J497DW all in one.  It is also a brscan4 printer (I think)  
I installed the printer and scanner driver for the new printer from the Brother webpage.  
Both  printers work fine.  
Now, the new MFC-j497dw scanner works fine and the old MFC-7620 cannot be found.  :(  
I've tried the fixes mentioned and they don't work.   They did work when I upgraded to Ubuntu 18.04 and I lost the older MFC-7820.

---

