---
title: "Installing software without internet?"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by jedimattk on 2009-09-27
Greetings--

My friend has just switched over from Windows XP to Xubuntu. His main complaint since switching is that he cannot install software from his house, since he does not have an internet connection. The best way we have found so far is to cart his Optiplex to my house, connect to my wireless network, and download software - hardly a feasible everyday option.

The problem, of course, lies with dependencies. I have tried APTonCD, but since I have a different Linux distro than he does (I'm running Mint 7), that's not exactly the best course either. It seems like, if you could download all the dependency debs as well as the deb for the software itself, you could manually install everything. But is there some way to determine what dependencies a package will need before installing it? 

Thanks for any help you can provide - he's getting pretty frustrated with Linux, and if we can't help him, he will switch to Windows 7. The horror!!!

~Matt

---

### Post by davec64 on 2009-09-27
Nice and easy!

Get him to open Synaptic and Mark all the packages he wants to install (dependancies will be marked automatically).
Instead of clicking Apply go to the file menu and select "generate Pacakage Download Script".
Save the Script and run it on your machine to download his requierd packages.
Probably best to do this with a memory stick and you can them transfer them onto his machine when downloaded.

---

