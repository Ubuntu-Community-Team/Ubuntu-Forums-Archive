---
title: "ISA Sound Card (AD1816)"
date: 2008-10-07
forum: General Help
---

### Post by heart13252 on 2008-10-07
I'm having some problems getting sound to work on a very old PC for a friend.  I've taken the case off and found an **Analog Devices AD 1816** sound card inside.

After the initial installation, the sound is not working.  I've googled around a bit and have several pages which all contain the same information.  The problem is, I'm new to linux and have no idea where the following files are located.

Here is one of the pages that seem to be coherent but are too much for me to follow:
[http://manpages.ubuntu.com/manpages/intrepid/en/man4/snd_ad1816.html]("http://manpages.ubuntu.com/manpages/intrepid/en/man4/snd_ad1816.html")

I've no clue if I should compile this driver into the kernel (I'm not even sure how to do this anyway) or where the loader.conf(5) file is located in order to add the appropriate lines.

Anyway, thanks for any input you folks are able to provide.

Cheers,
Heart

---

### Post by heart13252 on 2008-10-07
After a bit more prodding around on these forums, I found that the loader.config file (not specifically loader.config(5)) was supposed to be located in:  /boot/loader.config
As is displayed in a post on [http://ubuntuforums.org/showthread.php?t=720927]("http://ubuntuforums.org/showthread.php?t=720927")

So, with the file absent from this location, do I only need to create it myself?

I'm sorry if I'm coming across seemingly absent minded but I do know a little when it comes to computers.  I just don't understand the *nix environment just yet.

Thanks again for any input folks have.
Cheers

---

### Post by user11 on 2009-01-18
Hey, I just got an ISA NIC to work, maybe this will help. I have a 3c509b-tp Ethernet card that wouldn't be recognized. I typed the following:

sudo modprobe 3c509

Then I typed my password and everything worked!

Hope this helps.

update: To keep from having to type "sudo modprobe" everytime you reboot, just add the device name to the list in the /etc/modules file (bottom of list).

---

