---
title: "Simple scan &amp; Xsane"
date: 2015-10-25
forum: Hardware
---

### Post by emacdonald on 2015-10-25
Upgraded to 15.10  and now Simple scan and xsane will not work with my Canon MG7150 (Networked) (it worked prior to the upgrade). Reinstalled all the drivers. No joy.
If I run the canon supplied scangearmp program it detects the scanner and works ok.

The error message via xsane is " Failed to open device pixma:MG7100_192.168...... invalid argument"

Ran the Strace  and have the log file, but to be honest it means nothing to me.
Anyone come across this issue?

---

### Post by honkir on 2015-10-31
Yes, I have exactly the same issue.

Update: solution (workaround) found: [http://askubuntu.com/questions/688642/network-scanner-canon-stops-after-upgrade-from-15-04-to-15-10/692359#692359](http://askubuntu.com/questions/688642/network-scanner-canon-stops-after-upgrade-from-15-04-to-15-10/692359#692359)

Found a thread that aims to debug it but still no solution: [http://askubuntu.com/questions/688642/network-scanner-canon-stops-after-upgrade-from-15-04-to-15-10/691855](http://askubuntu.com/questions/688642/network-scanner-canon-stops-after-upgrade-from-15-04-to-15-10/691855) . My own debugging effort led to about the same - using "SANE_DEBUG_BJNP=2 SANE_DEBUG_PIXMA=4 scanimage -T" and strace. So still no solution from me either. Just a workaround: ScanGearMP works for me (and so Gimp does which uses this fronted).

---

### Post by pqwoerituytrueiwoq on 2015-11-01
one post in the above link mentioned it is a bug in sane-backends
you can try a newer release with this ppa
[https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)
if you can't get it to work you can use a usb cable and share it via the front end software in my signature

---

### Post by emacdonald on 2015-11-01
Excellent used the workaround in 

[http://askubuntu.com/questions/68864.../692359#692359](http://askubuntu.com/questions/68864.../692359#692359)

"downloaded the 3 packages (libjpeg62-turbo_1.4.80-115-gfb907b2-1_amd64.deb, libsane_1.0.25+git20150927-1_amd64.deb, libsane-common_1.0.25+git20150927-1_all.deb) from debian experimental and installed them using sudo dpkg -i filename"

Many Thanks

---

### Post by eightbits2010 on 2015-11-04
I installed xsane but it does not work very well with my HP Scanjet 4400c scanner if that is any help. It worked twice withen 12-15 starts. I will probably have to keep my XP-PRO laptop
to keep a functional scanner.

---

