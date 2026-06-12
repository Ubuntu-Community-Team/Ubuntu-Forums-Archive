---
title: "HP Deskjet (print-copy-scan) :: Scan issues"
date: 2011-01-06
forum: Hardware
---

### Post by Ampi on 2011-01-06
I have a HP Deskjet 2020 J510. It is suppos to be able to print, copy and scan. I can get it all to work except for scanning.
I tried both Xsane en Simple scan. Both the programs are unable to find the scanner even though I know it is connected correctly and as a printer the system recognizes it.

Ive been looking around in Google and the forums, and it seems to be an issue that is solvable but complicated, changing config-files, filling in IP addresses, etc. 
I yet haven't found a thread of webpage that explains in a way that I actually understand or am able to follow. 

Can anyone help me make my scanner visible to Xsane, Simple scan or another alternative? I also installed HPLIP Status Service.

---

### Post by Ampi on 2011-01-10
Im a bit closer to the solution..

I went to the HP site for my product. There you can download drivers for linux. It's a .run file and when you run it, there (probably) will be some dependencies missing that you need to install. Then run it again untill the installer finishes. It could be that the installer finishes, but there are still some OPTIONAL dependencies missing. Install these too and run it again. If you don't, some functions like scanning or faxing might no get installed and wont function. 
A tip: Most packages have a different name then the name the installer is searching for. All -devel packages are now -dev packages. What I did (and worked) was go to the Synaptic Package Manager and download pretty much anything that had a similiar name (with some help from google).. :)

Still the scanner is not found by both XSane and Simple Scan.. :(

---

### Post by Ampi on 2011-01-14
Finally it works.

For anyone that cares. What I did is the following:
1. Download the HPLIP that corresponds to my all-in-one model.
[http://hplipopensource.com/hplip-web/recommended.html]("http://hplipopensource.com/hplip-web/recommended.html") Choose the model of your printer here and check if everything is supported, click and download the corresponding HPLIP. Follow instructions. 
2. Once it is all installed I changed in the Printer Properties the "media source" to "main tray" and then when I started XSane it suddenly worked.
Remember if tou want to print I think you have to change the "media source" "Auto-select" again, im not sure though. 

I hope it can help someone else.

---

