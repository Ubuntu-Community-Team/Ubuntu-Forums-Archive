---
title: "My digital life is dying... please help.... please?"
date: 2010-08-07
forum: Hardware
---

### Post by Westz on 2010-08-07
okay ive got a few problems (my computer life is a horrible wreck at the moment.) 

first off, i'm writing this from a Dell Latitude D610 booting Lucid from the CD. im booting from the CD because about 2 weeks ago, my hard drive's boot sector got corrupted. it also seems its only the one sector, and ive had a few people tell me i can quarantine it by formatting my drive then partitioning off the bad sector. so i ask you all, is this a good idea? or will i end up murdering my drive in the long run? all my personal data is intact, it seems only a very small portion of the drive is corrupt, and i dont have the money to replace the drive. 

if i end up doing this, i'm going to need to back some things up. about 20gb worth of data. so my question is how do i back it up? i dont have a stable internet connection due to my router being crap, and i dont have any large storage devices besides my desktop's hard drive, but that has no way to connect to my laptop. i've been hoping i can set up an ad hoc network and fileshare everything, but that leads me to my last problem.

i cant seem to get wifi to work on this laptop. the built in wireless card wont turn on in ubuntu. i've installed the windows drivers for it with the ntdiskg utility, and nothing. it says i have hardware but for some reason i cant use it. also, i have a netgear WG111 v3 external wireless adapter that seems to work fine in windows but (suprise) not in ubuntu (unless the AP happens to be a netgear router)

so if anyone has any ideas, ways to help, general insights suggestions, etc, i strongly urge you to email me, as i cant get on to the forums regularly, but i can check email from my phone. again, any help is strongly appreciated, 

Westz

[EMAIL="cvw171west@hotmail.com"]cvw171west@hotmail.com[/EMAIL]

---

### Post by tgalati4 on 2010-08-07
Get an external drive and use the Live CD to backup your data.  You could also use a couple of 16 GB flash drives.

Try fixmbr--do a search in the forums for how to do that.  If it works great.  If it doesn't, then at least you have a backup of your data.

---

### Post by Westz on 2010-08-07
sorry to be so sarcastic, but i've already stated im rather broke. how do you suppose i can afford two 16gb flash drives? thats more than buying a new laptop harddrive and letting the local computer store back it up for me

---

### Post by wookieshaver on 2010-08-08
I think the simplest way would be to plug in an ethernet cable to the laptop and to the router your desktop is using. (hopefully it is a router or at least a modem with a usb and a ethernet connection - usb to pc ethernet to the laptop in that case). You would continue to use the live cd and manually transfer the files to a shared folder on the desktop pc. Assuming the desktop is a windows pc (or even if it isnt and youve created a share folder in whatever OS it is) you could then transfer the files using samba within the live cd session. Copy - paste - wait a really long time.  Hope this helps - if you dont have a spare network cable or router perhaps a friend does!

---

