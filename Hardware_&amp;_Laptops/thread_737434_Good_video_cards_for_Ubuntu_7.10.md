---
title: "Good video cards for Ubuntu 7.10"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by Sinja on 2008-03-27
My video card is pretty ok. It is an ATI Radeon X600. However, i tried to run Team Fortress 2, and the quality is.... well... it's like Super Mario Bros. And it is very laggy.

I was wondering what kind of new video card I should get.  I want really good graphics, so a more recent one is much preferred. And my PC uses the whole PCI system.

Any suggestions?

---

### Post by Rocket2DMn on 2008-03-27
Any newer video card would provide an increase in performance, but you may be able to get better performance out of your card.  Are you using the restricted fgrlx drivers?  Do you disable Compiz Fusion before you play?  See:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
and to disable compiz when you play, run
```
metacity --replace
``` then to load it back run ```
compiz --replace
```

---

### Post by SGAZ on 2008-03-28
I just built a new machine and installed Gutsy within the last few weeks.  I'm using an **ATI HD3850 **and had to install the new 8.3 drivers from ATI because the Ubuntu Restricted drivers did not recognize my card.  That being said, I'm now running Compiz-Fusion and I'm pretty happy. So there is the endorsement part :)

You said, "***And my PC uses the whole PCI system***." If you mean PCIx then you will be fine getting a new card. However, if you meant PCI then you might be upgrading more than just a video card to improve your graphics performance.

Good Luck

---

### Post by Sinja on 2008-03-28
Thanks everyone.

And yeah, i have PCI express. I didn't read that right.

And before i switched, the games still had to be played on relatively low settings. I would rather have them maxed out.

And from what i read on the forums, Nvidia cards are the way to go.

Now the question is, "what Nvidia PCIx card should i get?"

---

### Post by SGAZ on 2008-03-28
I would look at the current "Nvidia Restricted Drivers" to see what version of the Nvidia driver they are using and then check what cards are currently supported in that driver release.  That would be the safest, surest, least frustrating, and probably most economical way to move forward.

It's no fun buying an expensive and  ragin' video card then having to wait for somebody to write Linux drivers for it :)

Good luck!

---

### Post by Bllasae on 2008-03-29
Well, you've basically already screwed yourself with the whole "gaming laptop" thing. The laptop is not meant for gaming, no matter what anybody says, and therefore most/many of the graphics cards worth buying are for the Desktop computer.

---

### Post by Sinja on 2008-03-29
gaming laptop? i dont remember saying anything about a laptop. this is a desktop. And thank you very much SGAZ. But where do i find "nvidia restricted drivers"?

---

### Post by Zimmer on 2008-03-29
Not sure about that, but a look here may help a bit
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
and I have been using this a s a rough guide to the abilities of various cards  
[http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-X3100.2176.0.html](http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-X3100.2176.0.html)
not sure if there is a desktop equivalent page...  must go look...

---

### Post by kaivalagi on 2008-03-29
For restricted drivers you'll need to install the restricted driver manager:

```
sudo apt-get install restricted-manager
```

I have the restricted drivers installed on my 7.10 desktop for my 8800gts, and I have no issues, I am running the xgl xserver too. The version I have is 100.14.19, quite old these days.

You may want to consider installing hardy 8.04 anyway, as it comes with restricted nvidia drivers at version 169.something, these will support the newer nvidia cards.

Alternatively if you hit issues with the restricted drivers you can install Envy. Envy will manage the download, build and install of the latest nvidia drivers for you, you don't want to have to do this yourself! It's not pretty. I have used Envy for my media center box which has nvidia 7100 on board, something quite new, and this works just fine.

Envy can be downloaded here, and supports both 32 and 64 bit:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

Hope that helps

---

