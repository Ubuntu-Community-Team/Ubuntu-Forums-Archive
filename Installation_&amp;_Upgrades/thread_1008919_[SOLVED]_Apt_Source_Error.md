---
title: "[SOLVED] Apt Source Error"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by frankleeee on 2008-12-12
So I installed Jaunty with the desktop CD no problems. I then started the usual adding of programs from add remove for media codecs etc. I made the mistake of trying to add the medibuntu repository and key to the apt source list while the add remove was installing. So now I can't access synaptic update or open add remove. I have run the  
sudo dpkg --configure -a and the  sudo apt-get install -f commands all correctly I believe. 

**Here is the error I get from trying to open add remove.**
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
[B]
Here is the error from synaptic[/B]
E: Type '--2008-12-11' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

**Here is the error from the software sources** which mentions medibuntu which is not in the apt/sources.list any more
E: Type '--2008-12-11' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: Unable to lock the list directory

I have also reloaded the apt source list from the CD 

Since I have never had to rely on error logs I have no clue what to look for.

This is a dual-boot along with intrepid for interest in jaunty, so a reinstall is no problem, I have nothing on this laptop besides the programs. I am not sure how to just overwrite the jaunty install again and save the intrepid if possible.

---

### Post by frankleeee on 2008-12-12
So I just reran the medibuntu install and the key install and this cleared everything up although I have some gedit .d list and gpg error files that are root and can't remove. Everything seems to be working though.

---

