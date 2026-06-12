---
title: "Lenovo T60p no fgl_glxgears"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by banjomark on 2006-06-17
Hi All-

So I have a new T60p with the ATI FireGL 5200.  I've got everything working on   the system (including the fingerprint reader...so sweet), and to some extent the fglrx driver even works (I can run at 1600x1200).  However,  I can't run fgl_glxgears (and on a related note, I can see the display "paging", where it's not so smooth at refreshing...seems like it's the driver).  So, here's the output of fgl_glxgears:

# fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32
#

And the relevant portion of the xorg.conf file is:

Section "Device"
        Identifier      "ATI Technologies, Inc. ATI Default Card"
        Driver          "fglrx"
        ChipID          0x71c5
        BusID           "PCI:1:0:0"
EndSection

I've tried the fglrx driver from both the apt repository and ATI's website, but they appear to be in synch since the behavior is indistinguishable.

Thanks in advance for any help this great forum provides!
~Mark

---

### Post by buttari on 2006-06-19
Hi,
I have exactly the same laptop and it is working flawless. I think that you should remove the 
```

ChipID 0x71c5

```
 line from youe xorg.conf. That line, in fact, is useful if you are still using 8.24.8 drivers because they don't officially support you graphic card. The new drivers (i.e. 8.25.28) support it so upgrade if you didn't!
Regards
Alfredo

PS
can you point me to some documentation to enable the fingerprint reader?
thanks

---

### Post by compmodder26 on 2006-06-19
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader")

That is what I used.  I compiled everything to make it work.  For some reason the pre-made .deb wouldn't work for me.

---

### Post by banjomark on 2006-06-25
wow thanks- that fixed everything.  And I just used the same steps off thinkwiki for hte fingerprint reader.  After using it for a few weeks though, I decided it's kind of a pain, 'cause you have to get your finger "just right" to get it to work.  

Thanks for responding, sorry I was so slow to thank you!

~M

---

