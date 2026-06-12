---
title: "Bluetooth mouse stops responding on short idles"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by sdennie on 2007-07-25
I just bought a Targus Bluetooth Laser mouse and was able to install it and get it working without any trouble on my laptop with built-in bluetooth.  However, there is a problem in that, as soon as the mouse goes idle for about 5-10 seconds, the next time I move it, it won't respond for about 2+ seconds.  Here is what I've found out so far:

1) The 2 second delay is only in regards to the mouse movement.  A click or scroll wheel will cause the mouse to instantly be responsive.  When moving the mouse constantly, it works perfectly.

2) The 2 second delay gradually gets longer as the mouse is idle for longer periods of time.  So, if it's idle for more like 2 minutes, the delay can be up to 4 seconds.  Again, clicking doesn't cause the delay.  It's only movement.

3) The mouse documentation says that after 5 minutes of inactivity it will turn itself off.  I've verified that this is not happening on these delays because hidd --show still lists the mouse when it's been inactive for < 5 minutes (when I get the short 2 second pause) but doesn't list it when it's been inactive for > 5 minutes (when I get a much longer pause).

4) hcitool info shows that the mouse supports some feature named <power control> but, I don't know how to query or set this value (if that's even possible).

5) I've tried it with 2 different kernels and have had no luck.

I'll be happy to supply more detailed information if needed but, at this point, I'm mostly wondering if the symptoms I'm describing are something someone recognizes and knows how to fix.

Thanks.

---

### Post by tripinva on 2007-07-25
Is it the AMB03US?  If so, I have the same mouse and the same issue, but I think it's a feature and not a bug.

From what I can gather, it appears to be a power-saving feature.  I read the reviews on NewEgg before I bought it (from somewhere else) and others complained about the same thing.  The mouse does this under Windows too, IIRC.

I think that what it does is it stops using the laser to check for movement but every second or two, as this probably saves some amount of battery life.  I've already gotten used to it, despite only having it for a week and a half.

- Trip

---

### Post by sdennie on 2007-07-25
Yes, same mouse.  It sounds like a pretty poorly thought out feature to me.  I wonder if there is a way to disable it via software.

Thanks for your reply.

---

### Post by sdennie on 2007-07-25
I've figured out what the problem is and how to fix it.  It turns out that it's not the mouse but the internal bluetooth adapter.  I noticed with hcidump that 5 seconds after the mouse goes idle, the adapter is setting the mouse into "Sniff" mode.  I don't know what that means but, disabling that functionality causes the mouse to always respond instantly (though, it will probably still sleep itself after 5 minutes).  To disable the "Sniff" mode, turn off the mouse and then:

$ hciconfig hci0 lp

You should see something like:

hci0:   Type: USB
        BD Address: aa:bb:cc:dd:ee:ff ACL MTU: 384:8 SCO MTU: 64:8
        Link policy: RSWITCH HOLD SNIFF PARK 

What I did is just change the policy and remove the HOLD SNIFF PARK part (for some reason I wasn't able to just remove SNIFF):

$ sudo hci0 lp RSWITCH

Now the first command shouldn't show HOLD SNIFF PARK.  If you turn the mouse back on, after it reconnects, you should no longer have the restart delay after 5 seconds of idle time.

You will also need to find the corresponding section in /etc/bluetooth/hcid.conf and remove the hold,sniff,park part.

Hope that helps.

---

### Post by z0mbie on 2008-01-26
Hey thanks. This is actually what needed to be adjusted. Works perfectly.

---

### Post by morticul on 2008-02-27
Seriously, you just saved my mouse and it is really grateful to you. It was a few seconds away from the garbage and it now works like a charm.

Just a small correction:
$ sudo hci0 lp RSWITCH
should be:
$ sudo hciconfig hci0 lp RSWITCH

---

### Post by havoc_joe on 2008-04-19
Here is a decent description of these terms if anyone is interested:

Sniff mode: In sniff mode, the slave listens within its Piconet at a reduced scan rate (programmable).

Park mode: In park mode, the slave is still synchronized within the network, but doesn&#8217;t participate in data transmission. Devices in this mode only occasionally listen to maintain synchronization and for a wake up call. This is the maximum power saving mode.

Hold mode: In hold mode, only an internal timer circuit keeps on working. Slaves can request the master to allow them to go into hold mode

Source: [http://fmcsa-ts.dot.gov/PublicDocument/research/Bluetooth%20Wireless.pdf](http://fmcsa-ts.dot.gov/PublicDocument/research/Bluetooth%20Wireless.pdf)

~Joe

---

### Post by grobbins on 2008-04-30
Hi,
Same issue here. Thanks for the tips on solving it. I'm new to Ubuntu and, while I work in software, I'm not a programmer. Assuming these changes can be performed by non-programmers, would anyone have time to explain how?
Thanks,
Garth

---

### Post by forexero on 2008-06-01
thank you very much for this contribution.
i was in the same case

---

