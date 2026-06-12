---
title: "The cursed BCM4318 -- possible solution"
date: 2010-07-06
forum: Hardware
---

### Post by hwertz on 2010-07-06
I have one of the often-cursed Broadcom BCM4318 network cards in my Dell Inspiron 2200.  With ndiswrapper, this card works stably, but there are no fun modes -- no monitor mode, no access point mode, and so on.   With b43, it is fully featured but unstable as all hell (no kernel crashes, it will just drop off the network in any mode with no kernel messages or anything whatsoever.)  I wanted to run this as an access point!  One GOOD point, I found if I opened or closed the lid while under transmit load I could reliably break it -- so I could try things to debug it.  Ultimately, I think either the card is sensitive to interrupt delays or some kind of problem with DMA, which the power management "tickles".   A common solution people say is to turn off ACPI, but without ACPI my card doesn't get a useable interrupt, so this didn't work for me (plus I don't want it to burn that much power.)

     So, I installed hostapd-0.7.2 from source, and I installed the b43 driver from compat-wireless-2010-06-27.  I don't think either of these affected it, but since it's working for me now I'm keeping them, and I'll mention it so you don't do everything else and have it mysteriously still not work.
     edit: Yeah you need a newer b43, I just took a look and my stock b43 (from 2.6.32-23-generic) has no messages about TX Status at all.  Probably the wireless backports package will do the trick.

     What I found was, when b43 hangs, an "echo 1 > /sys/kernel/debug/ieee80211/phy0/reset" will succesfully get it back up without having to restart hostapd, or bring card back down or up, or set the card back up -- I guess mac80211 must take care of that.    And with verbose=3 flag, *and* open firmware, the b43 driver *actually* logs error messages when it hangs instead of just silerntly hanging  Oh joy, everything I need to fix it!

     What you WILL need:

1)     run an editor (as root) and add b43.conf into /etc/modprobe.d with contents:
options b43 btcoex=0 verbose=3

     The btcoex=0 turns off Bluetooth Coexistance mode, I don't think this is needed.  verbose=3 *is* needed -- this turns up debugging enough so a error is actually logged when the card hangs, otherwise nothing whatsoever is logged.

2) openfwwf-5.2 -- this is an open source firmware for the broadcom card, it installs into /lib/modules/b43.  You may want to back that directory up.  I needed to download b43-tools, and build the assembler from it.   "sudo make ; sudo make install" puts b43-asm and b43-asm into /usr/local/bin/, and "sudo make ; sudo make install" in the openwwf-5.2 directory puts the firmwares in /lib/modules/b43.  This doesn't help AVOID hangs, but the stock firmware silently hangs, while openfwwf makes the driver throw errors when it hangs.

3) My script.  Please see the attached file!   I placed it in /usr/local/bin/card-kicker, chmod +x and chmod +s (it needs root permissions to write into /sys/).   I put "/usr/local/bin/card-kicker" into /etc/rc.local.  Enjoy!  Instead of a card hang, I get a ~500ms ping spike -- MUCH better.  And please, to my eyes this script isn't terrible but I feel like I'm missing a more elegant way to do it, so please if someone rewrites it a little better let me know!

:popcorn:

     Principle of operation -- the script looks at the end of /var/log/syslog with tail, looking one line at a time for instances of "Out of order TX".  If found, it sleeps 1 second so the card can finish spazzing, then resets the card with the "echo 1 > ..." and then burns through any remaining instances of "Out of order TX" (so it doesn't reset the card like 20 times in a row, these errors tend to come many in a row.)

---

### Post by hwertz on 2010-07-06
They are small, so I am attaching the openfwwf-5.2 firmware.. I assume since it's GPL it should be fine.  I think then, you can get those and get the updated drivers via synaptic, instead of having to compile anything.  I can't attach .fw's directly so it's a tar.  Enjoy!

---

### Post by hwertz on 2010-07-07
Please disregard -- I haven't been able to duplicate either the lid generating this error, or this script actually fixing anything.   The card still just drops off now when it feels like it.

---

