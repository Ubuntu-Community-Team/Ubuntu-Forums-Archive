---
title: "Advice on fresh install"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by talking_walnut on 2009-02-17
Hi guys,

I want to do a fresh install on my desktop and am looking for advice on how to go about it. I've 2 requirements that I need to meet. 

The first is that I've a RAID array with a variety of stuff on it that I can't afford to lose. I previously thought that once I had reinstalled mdadm it would automatically detect the RAID and everything would be available again. Last time I tried this I lost everything I had stored on it :(. Luckily it wasn't anything important at the time. If I this time back up my mdadm.conf file and copy it to the fresh installation will this do what I want to do?

My second problem is that I want to wipe all the configuration files from my /home partition. I've a different version of linux installed at the minute so don't want to copy them over. I'm thinking I could just delete all hidden files in the directory. I think the command ```
rm -rf .??*

```will do this. Gonna run it from the Ubuntu Live CD before installing. Is there anything wrong with this that I'm not thinking of?

Hope ye guys are able to help. I miss my Ubuntu!

---

### Post by talking_walnut on 2009-02-20
Just thought I'd post a follow up in case anyone else has similar questions. Reinstalled last night and everything went smoothly.

After posting this I did a lot more searching and everything I found said mdadm should automatically find my RAID upon installation. As I mentioned earlier, I tried this before and it didn't work. But being the brave (and stupid) soul I am I decided to test it out. I ran the Ubuntu Live CD and installed mdadm on it. I was going to use a persistant USB installation but for some reason my PC has recently started refusing to boot from USB drive :confused:. I then "diff"ed the new mdadm.conf file that was created and the one I already had and the only difference was the date it was created. I figured it was reasonable to assume it was reasonable to assume it had correctly identified my RAID. I figured correctly :D

Next step was getting rid of all the config files I didn't want. I ran ```
ls -a .??* > fileList
``` first to check to make sure no files I wanted to keep were going to be deleted. Anything I noticed on the list that I wanted to keep (.bashrc, etc) I just renamed with the leading . . After that I ran ```
rm -rf .??*
``` and let it do it's thing. 

Finally I ran the Ubuntu installer and kept my fingers crossed. Everything ran smoothly and I'm now running 8.10 with all my important files intact :)

---

