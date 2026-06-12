---
title: "Yet another &quot;ndiswrapper&quot; problem"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by cleekjc on 2005-08-04
I have a Dell inspiron 9100 which I am trying to get the wireless "Dell true mobile 1350" working.

I did a clean format install and followed the directions here 

[http://ubuntuforums.org/showthread.php?p=125537#post125537](http://ubuntuforums.org/showthread.php?p=125537#post125537)

Upon this "sudo modprobe ndiswrapper" I get "FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted"


ndiswrapper -l = bcmwl5  driver present, hardware present

The inf and sys files came off my WinXP pro which work..........so they should be the correct drivers.....and I even connected to my access point in WinXP so I know its not a hardware problem........

It worked once but when I rebooted a second time the adapter in networking was not there and I have been getting the above fatal error ever since including now after a brand new shiny format and install.................... ](*,)

---

### Post by cleekjc on 2005-08-05
Well I snaged the 686 kernel off synaptic and now I can modprob and see the adapter in networking  \\:D/

---

### Post by joebrandt on 2005-08-15
[QUOTE=cleekjc]Well I snaged the 686 kernel off synaptic and now I can modprob and see the adapter in networking  \\:D/[/QUOTE]
 I have the same chip and have been able to activate it so that it can see networks but have nevero been able to actually log on and surf wirelessly.  I did manage to get it working in Suse 9.3 but switching between wired and wireless was a real bear.  My linksys B wireless has wep activated and I plugged the keys into every program known to Ubuntu and still no luck.

---

