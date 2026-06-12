---
title: "Size of / and home partitions"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Psyphre on 2009-04-29
Hi, Im planning to do a clean install of Jaunty soon,  but I'm getting tired of having to backup all my data beforehand, its such a hassle. So I'm considering having seperate / and home partitions. My question is how much space do I give '/' ?

I have 60gb, and I'm a bit worried that if i dont give enough to / im gonna have alot of trouble (installing new stuff etc),  but on the other hand I need every GB of space for my home as I like to store as much as possible.

How much does '/' need?

THanks!

---

### Post by logos34 on 2009-04-29
> **Psyphre said:**
> I'm a bit worried that if i dont give enough to / im gonna have alot of trouble (installing new stuff etc), 

How much does '/' need?

It depends on what kind of user you are (power, gamer, etc.), and if you want to have a lot of apps installed.

~10 Gb usually is plenty sufficient.  I have x64 ubuntustudio with a fair amount of a/v apps (but no graphics stuff) and mine's only 6.79 GB (of which 87% used).

You know, if you run out of space you can always run 

sudo apt-get clean

to clear out the .debs piling up, which takes up a lot of room

Either that or boot the live cd and use gparted to shrink /home some and give the space to /.

---

### Post by Psyphre on 2009-04-29
thanks for the prompt reply.

This is where I am a bit confused:

System monitor says I have 51gb partition. 
Home takes up 28gb.
Since I only have 3gb free that would mean my '/' takes up 20gb!
Which is alot. Too much, I dont quite understand why that is.

I have no games installed (apart from windows games via wine, which install to the home directory) and I dont have loads and loads of applications installed.

---

### Post by logos34 on 2009-04-29
run this in a terminal:

df

what does it show?

---

### Post by SuperSonic4 on 2009-04-29
df -h will give the same result as df but will use gb making it easier to understand

on my laptop I have 18gb for /home, 2gb for swap, 5gb for /var and the rest for home

---

### Post by logos34 on 2009-04-29
> **Psyphre said:**
> 
Since I only have 3gb free that would mean my '/' takes up 20gb!


I wonder if you maybe have some stuff squirreled away in root trash, or some temp folder.  just a guess

---

### Post by Psyphre on 2009-04-29
Hi, I get this when I type in df -h


```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              52G   45G  4.0G  92% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  328K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M 1012M     0 100% /dev
tmpfs                1012M  1.7M 1010M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/scd0             7.6G  7.6G     0 100% /media/cdrom0
/dev/sdb1             233G  233G   35M 100% /media/Storage
```

---

### Post by logos34 on 2009-04-29
If home directory is taking up 28 gb, then it looks like your / files are ~17 gb--still seems excessive.

Again, some people find they have a crapload of discarded files in root trash, so you might try:

ctrl + F2

gksudo nautilus

View>Show hidden files

>/root/.local/share/Trash


And check size of deb cache:

du -sh /var/cache/apt/archives

---

### Post by Psyphre on 2009-04-30
I checked out the trash folder in root and there isnt even one. So I assume therefore its 0gb?

I realised there was an error in my calculating. I just copied over the whole home folder to an external and unlike system monitor which claims theres 28gb, it shows as 38gb when copying it to an external.
I have no idea why there is such a discrepency, but if I assume 38gb then my / is taking up around 14gb which is alot more realistic. But like I said, im not sure which is the true figure :S


If I were to assume 14gb, then would a 20gb partition be plenty for / ? With the rest for home.

---

### Post by logos34 on 2009-04-30
sure, 20gb should be more than plenty...But even ~14gb sounds like it's way to big for system files only.  Wonder what's in there (or like you say maybe the figures are wrong?)

---

### Post by Psyphre on 2009-04-30
oh really? how can i find out whats taking up so much space?

---

### Post by logos34 on 2009-05-01
> **Psyphre said:**
> oh really? how can i find out whats taking up so much space?

> du -k / | sort -nr | less

will list all your dirs, largest to smallest

---

### Post by Psyphre on 2009-05-02
thanks. I went thru with the reformat and gave 20gb to / with the rest to home.

Thanks for the advice everyone.

---

