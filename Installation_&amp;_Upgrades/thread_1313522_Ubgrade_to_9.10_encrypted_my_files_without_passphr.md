---
title: "Ubgrade to 9.10 encrypted my files without passphrase"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by KuroKuma on 2009-11-03
I installed Ubuntu 9.10 today from the Alternate CD. Going through the process like I do every time.  I use manual partition to select my / /usr /var and /home directories and chose to format everything but /home.  I used the same username that I always use.  When finished I rebooted and got an error upon logging in that it could not write files for Nautilus.  I rebooted into recovery mode and found my home directory was was not writable by me so I chmod u+w /home/username and reboot again.  This time around I log in fine but all of my old files (80 gigs worth) are encrypted into a ~/.Private folder.  I found this to be quite odd because I did not wish to encrypt them and the install did not ask for a passphrase.  There were links in my home folder that were broken README.txt and "Access Your Private Data" so I installed ecrypt-utils and was able to open the README.txt file and it said to type ecrypt-mount-private to mount my .Private directory.  I do this and it says

ERROR: Encrypted Private directory is not set up properly.

Why did it encrypt my files when I did not ask it to do so and is there any way of recovering my data?

---

### Post by mrauscher on 2009-11-20
WTF? I'm in the same boat. I've done this the same way for every version upgrade before: install the new version, formatting /, leaving /home unformatted, and everything has always come up fine. 

This time, with 9.10, it appears ~/ has been encrypted without warning (or none that I saw, anyway) and I'm stuck with an inoperable system. Any ideas short of wiping out my /home and starting everything from scratch?

---

