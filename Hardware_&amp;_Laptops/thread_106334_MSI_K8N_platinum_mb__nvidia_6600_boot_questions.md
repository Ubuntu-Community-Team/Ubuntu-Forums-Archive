---
title: "MSI K8N platinum mb / nvidia 6600 boot questions"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by mrrs on 2005-12-20
I recently purchased the above combination, and in trying to run the 5.10 live cd, the video is  displaying incorrectly. ( hard to describe, but more or less random color stripes and such, but basically unusable ) The store assures me that this is because "Linux doesn't support pci express". I chose this mb because what little I could find on the web indicated that people have had success with it. There is no copy of windows on this computer, so I have no way of definitively telling him that the card is defective. Should the live cd at least show me a desktop, or does something need to be tweaked, or is he in fact correct about the PCI express support?

I have tested the CD in another 64 bit machine, and it does work.

any suggestions would greatly appreciated!

markus

---

### Post by Sutekh on 2005-12-21
When do the random stripes occur?  Does the LiveCD get into a desktop?  

Does it look like this?
[http://ubuntuforums.org/showthread.php?t=104247&highlight=thrashed+display]("http://ubuntuforums.org/showthread.php?t=104247&highlight=thrashed+display")

If so, this is an issue that can be fixed by installing the nvidia binary drivers, you can do this on the LiveCD to try, or install it Ubuntu and then fix the problem.

I have a 6600GT PCI express (with MSI K8N), so I can say that Ubuntu does support those cards.

---

### Post by mrrs on 2005-12-31
The screen does not display anything like a desktop. I don't recall getting far enough to allow me to install the binary drivers from the live cd. Are there instructions somewhere on how to do that? I have since done a text install and installed the nvidia binary driver, which did indeed fix the problem.

---

