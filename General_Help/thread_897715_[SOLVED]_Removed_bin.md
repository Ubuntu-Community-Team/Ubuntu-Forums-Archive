---
title: "[SOLVED] Removed /bin"
date: 2008-08-22
forum: General Help
---

### Post by jasex on 2008-08-22
Sorry, to be an idiot, but I was trying to delete another file but accidentally beefed up and removed /bin

Can I fix this somehow... chrooting from a live cd or something?

---

### Post by Dr Small on 2008-08-22
How did you remove it? With:
```
sudo rm -R /bin
```

or via Nautilus?

---

### Post by coffeecat on 2008-08-22
If you removed /bin with 'sudo rm' you could boot up from the live CD and copy the live CD's /bin to your hard disc. That should get you a working Ubuntu back (no promises), but you might experience some version discrepancies between what you copy from the CD and what Synaptic/apt-get thinks is installed.

**Edit:** this is the output of ls from my (up to date) /bin folder if it's of any help:

> bash
bunzip2
bzcat
bzcmp
bzdiff
bzegrep
bzexe
bzfgrep
bzgrep
bzip2
bzip2recover
bzless
bzmore
cat
chgrp
chmod
chown
cp
cpio
dash
date
dd
df
dir
dmesg
dnsdomainname
echo
ed
egrep
false
fgconsole
fgrep
fuser
fusermount
grep
gunzip
gzexe
gzip
hostname
ip
kbd_mode
kill
ld_static
ln
loadkeys
login
ls
lsmod
lspci
mkdir
mknod
mktemp
more
mount
mountpoint
mt
mt-gnu
mv
nano
nc
nc.traditional
netcat
netstat
ntfs-3g
ntfs-3g.probe
pidof
ping
ping6
ps
pwd
rbash
readlink
rm
rmdir
rnano
run-parts
sed
setpci
setupcon
sh
sh.distrib
sleep
stty
su
sync
tailf
tar
tempfile
touch
true
ulockmgr_server
umount
uname
uncompress
vdir
which
zcat
zcmp
zdiff
zegrep
zfgrep
zforce
zgrep
zless
zmore
znew

---

### Post by jasex on 2008-08-22
sudo rm -rf /bin, meant to do sudo rm -rf ~/bin

:D But, I tried copying /bin over, and it won't start GDM... and I can't login into any TTYs

---

### Post by jasex on 2008-08-23
Screwed, ain't I?

---

### Post by sdennie on 2008-08-23
Even if you were able to get the machine working by copying from a live CD, I would still advise you to re-install.  Make a backup of /etc and /home and it's actually not very painful to re-install (I've heard that Hardy can preserve /home over a re-install now but have not verified this).

---

### Post by LateNiteTV on 2008-08-23
if i were you, i would alias rm to be "rm -i" so that you can confirm that you really want to do the rm.

---

### Post by jerome1232 on 2008-08-23
You shouldn't have used sudo to remove something under ~/, it would've saved you in this case.

---

### Post by LateNiteTV on 2008-08-23
imo you should never use sudo to begin with...

---

### Post by jasex on 2008-08-23
that'd be great, but it was extracted via sudo, so it had to be removed with sudo... I had to extract with sudo, or else it would suffer extraction errors.

my /home is on a seperate partition. could I just back up /etc to inside the /home/thursday, and just set it to be remounted during install, and then copy it over?

---

### Post by jasex on 2008-08-24
??? This shall be marked as solved, although, still debating if I should continue using 64Bit or just use the 32 bit livecd I am using... I quite enjoy the enhanced performance of using my 64bit processor.

---

