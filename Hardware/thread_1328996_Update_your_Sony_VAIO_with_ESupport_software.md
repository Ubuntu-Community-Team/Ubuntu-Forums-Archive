---
title: "Update your Sony VAIO with ESupport software"
date: 2009-11-17
forum: Hardware
---

### Post by mister_playboy on 2009-11-17
Sony releases driver updates and software patches for Vaio computers at their [[COLOR="SeaGreen"]ESupport website[/COLOR]](http://esupport.sony.com/) (US version in link)

If you have installed Linux on your computer, you will not be able to take advantage of these updates because the installer will refuse to run in WINE... it will error out during the model check, regardless of WINE's settings.

By using the program [[COLOR="Green"]Universal Extractor[/COLOR]](http://legroom.net/software/uniextract) in WINE, you can extract the actual software installation .exe from inside the .exe that you download, and this will run just fine in WINE... I have twice updated the firmware for my CD/DVD drive this way with Ubuntu installed.

I cannot guarantee this will work for you, and a botched firmware update could cause your hardware to become unusable.  **[COLOR="Red"]Use this method at your own risk![/COLOR]**

Further, extracting the executable in this way will bypass the step where you agree to the software's EULA.  If you are not okay with that, **then don't use this method!**

1. You will need WINE installed.
2. Download Universal Extractor (link above) and install it using WINE.
3. Download the software you want to use from Sony.
4. Open Universal Extractor and use it on the .exe you downloaded.  The default choice of extraction method should work.
5. A folder will be created in the same directory as the original .exe, with the same name.  In this folder should be a folder named TEMPEXEFOLDER, and inside that is the .exe that actually installs the Sony software.  Run this .exe in WINE.

The software should install correctly.  In my case, I was able to confirm the firmware of my drive updated with:

```
sudo lshw -C disk
```

I hope you find this method useful!  :p

---

