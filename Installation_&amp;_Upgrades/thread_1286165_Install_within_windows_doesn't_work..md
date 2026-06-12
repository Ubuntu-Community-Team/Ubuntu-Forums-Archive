---
title: "Install within windows doesn't work."
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by praveenthivari on 2009-10-08
Hi,
    (Using Win 7 at present, but I like to try Ubuntu)
    I have downloaded ubuntu 9.10. and mounted it on a virtual disk .
    It came up with the option to run wubi.exe.
    Initially, I installed in a different partition than that containing Windows.It installed fine and was working fine but then I had to uninstall it.
    and, now i am trying to install it again in the same drive as I did previously, but it doesn't get installed.

Process goes like this:
    During my last installation it took at least 5-10 min to extract everything to the drive but now it appears like it extracts everything within few seconds and asks for reboot. On reboot it installs the OS in 1-2 min and on booting again I get dual options. On selecting the ubuntu it stays blank with following line:

boot:/

---

### Post by mikewhatever on 2009-10-08
Looks like a W7 issue, which we don't really support here.

---

### Post by praveenthivari on 2009-10-09
Thanks. for such a good article and of course for your thoughts on the problem. I'll try to solve it myself and if i get any solution I'll report back:P:P:P

Update:
I think I got the problem. It is with Wubi Installer of Ubuntu 9.10 because I have now installed 9.04 inside W7 and it works. But now I am plagued with new problems the mp3 codec and the update arhieves show  error message something like this:

"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."


Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mikewhatever on 2009-10-09
Well, congratulations, and hope the devs fix wubi 9.10 for the final release. There can be two problems, the repository is downor no longer available, or something is wrong with the internet connection in Ubuntu. If it is the repository issue, try System->Admin->Software Sources and just pick another server. If it is the internet on Ubuntu issue, post some info about your hardware.

---

### Post by praveenthivari on 2009-10-09
> **mikewhatever said:**
> Well, congratulations, and hope the devs fix wubi 9.10 for the final release. There can be two problems, the repository is downor no longer available, or something is wrong with the internet connection in Ubuntu. If it is the repository issue, try System->Admin->Software Sources and just pick another server. If it is the internet on Ubuntu issue, post some info about your hardware.

  Thanks for the info. i changed my server to Main server from the local ones and 'WOW' it's downloading all the updates. 
Once again thank you.:P:P:P

---

