---
title: "sudo dpkg --configure -a hangs"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by dcroxton on 2009-09-04
My computer (running Jaunty) hung on the last upgrade, so I had to reboot it.  Afterward, I had to run sudo dpkg --configure -a before I could do anything with packages.  The problem is, it also keeps hanging, always on a mono package.  Mono seems to launch its own thread, which I think is what is really causing the computer to hang.  When I run ps -Af, I get the following (besides a lot of other stuff, including the dpkg thread):

```
7940 pts/0    00:00:00   mono-gac.postin
 7941 pts/0    00:00:00     gac-install
 7971 pts/0    00:00:00       gac-package-ins
 7973 pts/0    00:00:00         mono
 7974 pts/0    00:00:00           sh <defunct>
 7978 pts/0    00:00:00           sh
 7979 pts/0    00:00:00             mono

```

Apparently I was foolish to install mono-develop recently.  I can easily live without it, but I need to know how to get past this dpkg error.  If there is any file I can manually edit so dpkg won't keep trying to process it, I would be happy to do that.  I removed all the files from /var/lib/dpkg/updates based on a forum post, but that didn't help, and I don't know enough about the other files to know what to remove (if that is indeed a way to solve it).

---

### Post by tommcd on 2009-09-05
Try running:
```
sudo dpkg --clear-avail && sudo apt-get update
```
If you can then get updates and install packages, then you are ok. If not, then try running:
```

sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```
See this thread:
[http://ubuntuforums.org/showthread.php?t=1022727](http://ubuntuforums.org/showthread.php?t=1022727)

---

### Post by directhex on 2009-09-05
Which release are you running? I've seen rare reports of gacutil freezing, but never been able to reproduce

---

### Post by dcroxton on 2009-09-05
tommcd:
sudo dpkg --clear-avail returned no messages, sudo apt-get update ran for a while updating, but ended with the usual 'dpkg was interrupted, you must manually run dpkg --configure -a'.  Sudo apt-get -f install returned the same error.

Any other ideas?


directhex:
I'm running Jaunty (9.04).

---

### Post by motorna_testera on 2009-09-05
i have the same problem
[http://ubuntuforums.org/showthread.php?t=1258942](http://ubuntuforums.org/showthread.php?t=1258942)

---

### Post by tommcd on 2009-09-06
> **dcroxton said:**
> 
Apparently I was foolish to install mono-develop recently.  I can easily live without it, but I need to know how to get past this dpkg error.  If there is any file I can manually edit so dpkg won't keep trying to process it, I would be happy to do that.  I removed all the files from /var/lib/dpkg/updates based on a forum post, but that didn't help, and I don't know enough about the other files to know what to remove (if that is indeed a way to solve it).
Try removing monodevelop from the terminal with apt-get. 
```
sudo apt-get remove --purge monodevelop
```
If that does not work, post the error message that you get here.
Then try:
```

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```
Post any errors here.

---

### Post by agerfe on 2009-09-06
I have exactly the same problem.
Update hanged at "Installing 7 assemblies from libmono-addins2.0-cil into Mono"
sudo dpkg --configure -a gets to the same line and hangs.

---

### Post by agerfe on 2009-09-06
I just solved my problem.

I found these threads...

[http://ubuntuforums.org/showthread.php?t=1229506&highlight=update+failed]("http://ubuntuforums.org/showthread.php?t=1229506&highlight=update+failed")

[URL="http://ubuntuforums.org/showthread.php?t=1259220&highlight=public+key"]http://ubuntuforums.org
/showthread.php?t=1259220&highlight=public+key[/URL]

... and I did this:

1. I opened a terminal and called nautilus > sudo nautilus
2. Then I browsed to /var/lib/dpkg/info/ and - **after making a copy of the folder** - I removed all files associated with mono-gac (mono-gac.list, mono-gac.md5sums, mono-gac.postinst & mono-gac.prem) and named the copied folder as info-original
3. Then I went to the terminal and run > sudo apt-get clean all
4. Then > sudo apt-get update
5. The update process failed and I got this message "GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783"
6. I run > gpg --keyserver subkeys.pgp.net --recv 2EBC26B60C5A2783
7. An then > gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add - 
8. Then I run again > sudo apt-get update
9. This got me to another error and a message that I should run > sudo dpkg --configure -a
10. I did and the problem was solved at last!!!

Hope this helps.

---

### Post by motorna_testera on 2009-09-06
i resolved a problem with steps 1. 2. 3. 4. and 9. :D
thanks very much!

---

### Post by directhex on 2009-09-06
Can you pastebin those /var/lib files from your info-original?

---

### Post by dcroxton on 2009-09-06
Thank you thank you thank you.  That solved it.

Sincerely,
Derek

---

### Post by ztomic on 2009-09-11
```
#sudo mv /var/lib/dpkg/info/mono-gac.* /root/
#sudo dpkg --configure -a
```
Seems to have worked here. /root/mono-gac.* can be deleted after the fix is varified.

---

### Post by directhex on 2009-09-11
> **ztomic said:**
> ```
#sudo mv /var/lib/dpkg/info/mono-gac.* /root/
#sudo dpkg --configure -a
```
Seems to have worked here. /root/mono-gac.* can be deleted after the fix is varified.

Except the bug will never ever ever be fixed unless someone actually reveals the contents of those "bad" files to the packagers.

---

### Post by Locke_99GS on 2010-09-27
dpkg was hanging on man-db after the power failed during an upgrade on my server. From the info in this thread, I got the issue resolved. 

```

sudo su
mkdir /var/lib/dpkg/info-orig
cp /var/lib/dpkg/info/* /var/lib/dpkg/info-orig/
rm /var/lib/dpkg/info/man-db.*
apt-get clean all
apt-get update
dpkg --configure -a
apt-get install --reinstall man-db
aptitude safe-upgrade
exit

```

Thanks.

---

