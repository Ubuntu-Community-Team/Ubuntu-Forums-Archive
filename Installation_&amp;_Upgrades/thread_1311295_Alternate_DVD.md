---
title: "Alternate DVD?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by MartinsK. on 2009-11-02
Hello,

I'm going to upgrade my desktop computer which has very limited internet access. I planned to use just Alternate CD, but I found out it still takes to download a load of packages. I read somwhere in forums that DVD image would contain all the packages, so no internet would be required (is that true?). Yet I can find only Install/Live DVDs, no alternate DVD.
How (if) can I upgrade Ubuntu without using internet?

Help, please :)

---

### Post by prshah on 2009-11-02
> **MartinsK. said:**
> How (if) can I upgrade Ubuntu without using internet?

Well in theory, you can use the alternate CD to upgrade your system.

In practice: it's a different story.

I updated my home desktop via Internet. It took all night to download the packages (I have a relatively slow Internet connection), then about 3 hours to complete the upgrade. 

For my laptop, I downloaded the alternate CD (it's never in one place for so many hours). The download (direct, not bittorrent) took about 2.5 hours to finish; the upgrade took about 4 hours. At the end of the upgrade, however, I found that I had to download about 400MB of upgrades; that rather nullifies the usefulness of the CD path to upgrade.

There is no alternate "DVD" as such. 

If you have a slow but steady Internet connection then I'd suggest using that overnight to upgrade your system, rather than the alternate CD.

Or you can try a "daily build" version from [http://cdimage.ubuntu.com/daily/20091027/](http://cdimage.ubuntu.com/daily/20091027/) (The url will change daily) or [http://cdimage.ubuntu.com/daily/](http://cdimage.ubuntu.com/daily/)

This CD will contain upto date packages minimizing the need for Internet access.

---

### Post by ajgreeny on 2009-11-02
To be honest, I suggest you backup all your home partition or folder, download the desktop .iso for whichever version you want, ubuntu, kubuntu, or xubuntu, and then do a clean install.  You might even be lucky enough to find an iso on a computer magazine cover CD soon, if such a big download is a problem, but I don't know if latvia has any good linux/computer magazines

I am surprised that prshah had such a large secondary update download after doing the update from the Alternate CD, but whether or not that is normal, a clean install will give you a better chance to get things right, particularly the change to grub2, which seems to have caused a problem occasionally on upgrades.

---

### Post by MartinsK. on 2009-11-02
Hell... exactly what I suspected.
The desktop computer is located in my home in countryside with internet speed about 20 KB/s. Not good.

I will try to see some other options... somwhere I once read an advice to download all packages as debs, transfer them to the computer to be upgraded, and then start upgrading... probably I will see if it works for me.

Anyway, thanks for help, guys ;)


BTW... is that "daily" link just casual AlternateCD, just kept up-to-date? Yesterday I was somehow surprised, because I upgraded my laptop from the very newest AlternateCD... and the wizard still required to download about 600 MB! Actually I'm  little doubtful if it used the downloaded CD image at all.

---

### Post by prshah on 2009-11-02
> **MartinsK. said:**
> 
BTW... is that "daily" link just casual AlternateCD, just kept up-to-date? Yesterday I was somehow surprised, because I upgraded my laptop from the very newest AlternateCD... and the wizard still required to download about 600 MB! Actually I'm  little doubtful if it used the downloaded CD image at all.

When you pop in the CD, you will be prompted if you want to upgrade. If it didn't prompt, run the (as root/sudo/gksudo) "cdromupgrade.sh" file located in the root of the CD.

You will be prompted whether you want to download the latest files or if you want to use the files on the CD. You can choose "CD" to ensure that no files are downloaded.

600MB of updates off a daily build? I too doubt update-manager has used the CD.

---

### Post by MartinsK. on 2009-11-04
I don't get something... I did answer "No", when the installer asked wether it should use internet to get the newest packages. BTW, upgrading to Jaunty was similar - didn't allow to use net, but it still downloaded a lot of data.
Anyway. I'll try this once more on my dekstop computer tomorrow...

---

