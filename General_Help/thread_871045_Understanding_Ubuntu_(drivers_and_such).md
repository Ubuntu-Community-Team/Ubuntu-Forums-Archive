---
title: "Understanding Ubuntu (drivers and such)"
date: 2008-07-26
forum: General Help
---

### Post by merrygoround on 2008-07-26
Hi,

I'm having some difficulties adjusting to Ubuntu since I'm so used to Windows. With a little difficulty, I got Ubuntu up and running using this motherboard: [http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2775](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2775)

Since this board was designed to be used on a Windows machine, and all the utility software was written for Windows, are the now totally lost since I'm running Ubuntu?

For instance, if you look at that link, you'll see its ROHS compiant and has Smart and Safe features to manage and monitor the motherboard in Windows.

Now, despite the board using integrated ATI graphics, which I hear is usually more quirky to get running on Ubuntu, the motherboard SEEMS to be working fine. However, I can't use features.

Would someone have to write software to use these features in Ubuntu, or is it just not necessary?

In some ways, I feel like I over paid on a motherboard, if it doesn't use any of the features?

Are there any words of comfort out there? Or perhaps a point in the right direction in finding how I can utilize these features?

Thanks for reading.

---

### Post by pytheas22 on 2008-07-26
Linux tries to include as many drivers by default as possible...unlike Windows, where you need to install drivers almost every time you add new hardware, you rarely should need to install a new driver (which is usually called a "module" in the Linux world) in Ubuntu.

To get the most out of your ATI graphics, you should install the proprietary ATI driver (by default Ubuntu uses a free, open-source one, but it's not as powerful as the closed-source driver).  [envy]("http://www.albertomilone.com/nvidia_scripts1.html") is an easy way to do it (envy doesn't always work for every kind of ATI card; if it fails for you, there are other things to do, so let us know).

All of the other features of your motherboard should just be working...stuff like DDR2 memory speeds and PCI express don't need any special drivers in Linux; they "just work."  The only place were you may potentially need to do some hacking is with the audio...you may need to do some things to use all of the channels (but maybe not).  If there are other components of the motherboard that you feel are not working as well in Linux as they do in Windows, let us know and we can figure out what's going on.

I don't know what the "Smart and Safe" feature does exactly, but if you want to do things like monitor motherboard and CPU temperature from Ubuntu, take a look at this [page]("http://blog.mypapit.net/2008/06/monitor-temperature-from-ubuntu-linux-gnome-applet.html").

---

### Post by merrygoround on 2008-07-26
I have the Temperautes being monitored, but I don't believe they are accurate.  One is saying 77 degress C, which is very high. Whats the best way to make sure your temps are accurate?

I'm using this processor: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103257](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103257)

---

### Post by pytheas22 on 2008-07-26
> Whats the best way to make sure your temps are accurate?

Your BIOS should also allow you to monitor the temperature.  Look in there and see if it still thinks that it's 77 C.  Also how are you currently monitoring the temperature in Ubuntu--are you using the Gnome applet or something else?

---

### Post by merrygoround on 2008-07-26
gnome applet and hardware monitor.  they unfortunately both read a temperature of 77C (but it does not specify if its the CPU or not - none of the temps are specifed).  The bios reads the CPU at a temperature of 32C.

---

### Post by pytheas22 on 2008-07-27
There are two applets in Gnome that can report temperature.  The first is called "Hardware Sensors Monitor" and I think is what you're using.  The second, and better, one is "Computer Temperature Monitor."  Try using the latter one and see if it still has problems.  In case for some reason you don't have that applet available, you can install it from [http://computertemp.berlios.de/](http://computertemp.berlios.de/) .

---

