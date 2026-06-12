---
title: "Changing the default shell on a Custom LiveCD"
date: 2008-08-14
forum: General Help
---

### Post by jpeirce on 2008-08-14
Alright, so I am in the process of creating a custom LiveCD based on the wiki here: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I have not had any problems throughout the whole thing until now, so far I have a working, bootable livecd thats stripped down the way I want it.

The last step would be for me to change the default login shell for the user that auto-logs in. I need to set the shell to a bash script I wrote that will run the scripts I want it to. 

Now, normally, I'd change /etc/passwd, but it looks like the user is being added when the livecd boots, and it doesn't already exist so I can't change the shell there. 

I have a hunch that the solution lies in the /usr/share/initramfs-tools/scripts/casper-bottom/10adduser script, but I can't figure out what I need to add to that file.

---

