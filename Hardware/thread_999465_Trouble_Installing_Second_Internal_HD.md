---
title: "Trouble Installing Second Internal HD"
date: 2008-12-01
forum: Hardware
---

### Post by utherpendragonfly on 2008-12-01
I'm not much of a tech person, but a friend of mine who is helped me build the computer I'm running Intrepid on. He also gave me a second HD which I installed last night. It shows up in Nautilus, but I'm unable to mount it. I get the message:

Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Did not revieve a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

It also says:
$MFTMirr error: invalid mft record for '$MFT' Failed to mount 'dev/sbd1' and... you have hardware faults, or you have a softRAID/fakeRAID hardware.

Now there is RAID hardware in there that is not set up, could that be what's causing the problem, or did I not connect it right? It seemed pretty simple... there was a connection for the power ribbon and the smaller red data ribbon that I plugged into SATA2 next to SATA1 where the first HD is connected. 

Can anyone set me in the right direction?

---

### Post by markbuntu on 2008-12-02
Did you format the drive yet?

---

### Post by utherpendragonfly on 2008-12-02
No, I have not (Duh!) I'm really new to this.
I've done a little more research since last night. I opened Gparted and it recognizes the HD. Now to reformat do I select bsd under the partition table settings?

---

