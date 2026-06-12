---
title: "Swiftfox installation problem"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by Accelerate- on 2009-10-04
Hello people, i've been having trouble installing swiftfox 3.5.3 and it's come to the point that it's beyond me (took about 3 hours since i just made a permanent switch to Xubuntu from windows yesterday)

So i downloaded the installer frmo the website and followed its instructions. Then i downloaded the .deb file and followed the instructions, then i googles how to install swiftfox and followed the instructions and got the same mesage all three times. 

"can't install swiftfox.sh"
"unable to read swiftfox.sh"

Each time it's basically been me downloading the installer and in terminal typing

Sudo apt-get update && sudo apt-get install-swiftfox3.5 
or something along the lines of that code.

Any ideas?

I also can't figure out how to uninstall firefox, do i just go through synaptics and select it for uninstalling?

---

### Post by Partyboi2 on 2009-10-04
One way is to add the repo to your sources.list. Open up Software Sources  and under the 3rd part software tab click on 'add' and add ```
deb http://getswiftfox.com/builds/debian unstable non-free
```then close Software Sources reloading the package list.
Then open up Synaptic and search for 'swiftfox-prescott' and install.

If you want to install the deb instead of adding the repo, download it from [[COLOR=Blue]here[/COLOR]]("http://getswiftfox.com/deb.htm") by selecting your processor at the bottom of the page. Once downloaded double click  on it to start the install process.

If you wan to use the installer then download the swiftfox.sh and make it excutable with
```
chmod  +x install-swiftfox.sh
```then run the script with
```
sh install-swiftfox.sh
```If you want to remove firefox search for it in Synatpic and remove it.

---

