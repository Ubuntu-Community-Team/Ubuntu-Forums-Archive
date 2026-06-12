---
title: "Getting the ATI/AMD drivers to work in Jaunty"
date: 2009-09-12
forum: Hardware
---

### Post by NexusZA on 2009-09-12
I know I know, ATI's support for Linux sucks big time. Thankfully though I have found a workaround that works really rather well for all those people struggling to get the FGLRX drivers to run properly in Jaunty.

The problem is in the fact that Jaunty (9.04)(and obviously the upcoming Karmic Koala(9.10)) use a newer version of X Server than Intrepid (8.10). This new version of X does automatic X config generation at startup of machine so that an Xorg.conf file does not need to be maintained. Unfortunately, it seems that ATI/AMD have decided as of yet not to release an update to the graphics drivers to account for the newer version of X.

Fortunately, amongst all this bad news there is some good. You CAN get Jaunty to work with FGLRX. This has actually happened to me on two of my machines, my desktop and a new laptop (on which I am typing right now), both of which have ATI cards and refused to work with a default Jaunty install. 

Here is the process. It is time consuming and not all that difficult, just stick to doing things in order and you should be ok:

1. Get an Intrepid (8.10) Live CD. You should still be able to download the ISO for Intrepid from the Ubuntu website, and then burn it to the CD.

2. Install Intrepid instead of Jaunty. Trust me on this just go through with this. Don't try to do anything funny yet just install Intrepid with default settings as if you were going to use it.

3. Once installed and you are booted into Intrepid on your machine, open a Terminal and do:

```
aptitude update
sudo aptitude install xorg-driver-fglrx
```

Say yes to all prompts and let it install the proprietary drivers for you then restart.

4. At this point you should have a machine running an older version of Ubuntu with a working 3D card and effects etc. But you want Jaunty right? No problemo. Go to terminal again and type:

```
sudo aptitude upgrade
```

This will get all available upgrades for Intrepid not yet installed. Once completed then do:

```
sudo aptitude dist-upgrade
```

This will now upgrade you from Intrepid to Jaunty.

5. Once completed you will reboot and should now be able to log into Jaunty Jackelope with your ATI card working.

Why this works? Well, I do not work for ATI nor am I an X developer but my thinking is that in Intrepid the installation of the ATI drivers creates the older xorg.conf file which allows the drivers to run properly. When you do a dist-upgrade, the new version of X takes the xorg.conf file generated into consideration when setting itself up and so ensures that the drivers continue to work properly.

Lets hope the Koala will have this issue fixed before release :)

---

