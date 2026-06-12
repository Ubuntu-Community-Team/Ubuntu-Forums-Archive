---
title: "Acer Aspire 3410 - Ubuntu 9.04"
date: 2009-09-08
forum: Hardware
---

### Post by Pauliepower on 2009-09-08
I recently bought a Acer Aspire 3410 with the intentions of dual booting Ubuntu and Windows 7. Now it's done, and I haven't found another thread about this model, I thought I'd help anyone else with this model by pointing out what works and what doesn't.

I should start by pointing out that at time of installation I only had an 8.10 disc, so installed using that and then used upgrade to bring it up to 9.04, so didn't really test 8.10. I can say that wireless works and the display is perfect. Also, Linux is not my first language so I'm not too knowledgeable, if I'm honest.

Under 9.04, the following didn't work straight away:
1. Ethernet: I found the fix for this on the Acer 3810 thread, and adapted.
How to make it work:
 - Go here  [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) and download "AR81Family-linux-v1.0.0.10.tar.gz".
 - Assuming it downloads to the deskop, follow this:
 ```

cd Desktop
sudo gunzip AR81Family-linux-v1.0.0.10.tar.gz
sudo tar xvf AR81Family-linux-v1.0.0.10.tar
cd src/
make
sudo make install
```Follow that with a restart. The guide on the 3810 thread mentions that it fails on the make install bit, and it did for me too, but after the restart ethernet came straight on.

2. Suspend/resume: It suspends ok, but turns the machine off if you go to resume.
3. HDMI out: Display manager can see it, but no picture was shown on my LCD tv. The VGA out does work fine, however.
4. Some of the apparent features of the touchpad don't work. The right hand scroll does, but that's about it. The 3810 apparently has the same problem.

Apart from that, everything else appears to work. Battery life is somewhere between 3 and a half to 4 hours with Powertop. Actually a very nice machine to use, was surprised considering the price!

Hope this helps anyone in the future.

---

### Post by SoftwareExplorer on 2009-09-08
Thanks--I'm trying to help someone who is new to ubuntu find a laptop or netbook that they like.  Also, welcome to the ubuntu forums. :)

---

### Post by karak_1984 on 2010-01-28
I have a Acer Apire Timeline 3810T and the touchpad dont work with all funcion. You can help me please....

---

