---
title: "Motherboard from MSI fuzzy GME965 heating issues and poor BIOS support"
date: 2008-08-06
forum: Hardware
---

### Post by Kubunteando on 2008-08-06
I want to post about my experiences while building a computer and I would like to know if you have had similar issues.

I wanted to build a silent computer for the living room but powerful enough so I could play some games. And at the same time using little power same as a laptop.

So I picked an ITX motherboard from MSI called Fuzzy GME965 based on Intel GM965 chipset and one of the few having a PCIEx16 slot. And I chose a Intel Penryn T9300 processor. All both components from the mobile computing world that use lower power and are more silent than desktop computers.

Everything worked great on the paper, but when I put everything together I found:

1- the CPU overheats. At idle runs at 65 Celsius, while in laptops the same CPU runs at around 47 Celsius.

2- no control of the FANs, so they never stop spinning.

3- no BIOS support for EIST (Enhanced Intel SpeedStep) to save power by using some sleep states and lower frequencies which is a basic feature in Mobile chipsets like the Intel GM965.

What I have done is to check that the thermal grease is enough and that the FAN and heat pipe is correctly installed. Both are fine.
I have also updated to the last BIOS version with no better results.

My best guess is that all 3 issues are related to the poor BIOS of the motherboard. Let's see what MSI says about it.

What I have learned from this is that the BIOS is crucial in your computer. The HW may support all the features you want but the BIOS needs to support them as well. And today usually only laptop manufacturers really take care of the BIOS features. So watch out when building your own computer.

Have you had similar overheating issues or problems with the BIOS?

How did you get them solved?

---

### Post by Kubunteando on 2008-08-08
I have reinstalled the heat sink and cleaned well the surfaces before applying new thermal paste.

Still the same overheating issue :-(

Still no answer from MSI :-(

---

### Post by Kubunteando on 2008-08-09
I will install in parallel Windows XP for comparison. I don't like to do this but I don't see any other way to get info.

I can run some tools in Windows to check the CPU and Core temperatures.

But no worries I will post here from Linux :-)

---

### Post by starcannon on 2008-08-09
I know that the Intel GM965 has no trouble with speed stepping, what I can't remember is if you need to compile the module or not.

A quick trial and error would be:

```
sudo dpkg-reconfigure gnome-applets
```

When asked
> Should cpufreq-selector run with root privileges?
choose **Yes**

Then R-click on either your top or bottom gnome-panel, choose 
**+Add to panel**
then choose 
**CPU Frequency Scaling Monitor**
then click
**+Add**
now click on the cpu scaling applet in the panel and see if it will let you set it to different presets. If so choose "On Demand" I think its called, you should have a cooler running cpu that only goes full throttle when required. If not your going to have to find the modules for the cpu and or chipset.

GL

P.S. Devs if you read this, CPU Frequency Scaling Monitor really needs to be simpler to set up, theres a nice gui to add it to the panels, but then one must know the secret squirrel code to actually use it.

---

### Post by Kubunteando on 2008-08-26
Well, the GM965 chipset supports it. But this issue is an example that the BIOS is key in a motherboard. And MSI is using a wrong BIOS:

- the BIOS is not supporting the GM965 power saving features
- the voltage is used for the processor is quite high for a Penryn processor which causes overheating

So this is a good example that you cannot trust the manufacturers, so read the reviews before buying a motherboard because the BIOS may not support the features of the chipset you expect.

One good way is to read the forums of the manufacturer. I have posted this issue there hoping MSI will do something about it.

---

### Post by Kubunteando on 2008-09-02
One month gone and no answer from MSI.
I opened the case with them one month ago and not answer...

What is more not even the support page is working! Already for 3 days!

Is this a serious manufacturer that is selling worldwide? What kind of support is this? Ah, yeah, a non-existing?

---

### Post by Kubunteando on 2008-09-13
I got some replies from MSI support. It seems they changed the Customer Support service during the summer, and simply they were not replying to the cases opened in the "old" way. If we would do so in my company I don't think I would be getting happy customers...

The latest news is that they are trying to point the CPU as the problem. It is a Penryn CPU of 45nm. And basically trying to deny that the BIOS is the problem. The CPU is forced to work at 2.5GHz when idle and MSI says that is not the problem for having 60 Celsuis when the CPU is idle.

I am going to test the same CPU is a HP laptop and see. Maybe that way they cannot deny the problem.

---

### Post by Stan.d on 2009-01-15
Any news on this isssue from MSI? (Got a similar system and the CPU is stuck with it's 'default' speed, no power saving features etc. available - under windows it works as intended..)

---

### Post by Kubunteando on 2009-01-16
I talked with MSI and the issue is definitely with the BIOS,
So there is nothing to do because MSI said they will not fix anything.

If your system works fine with Windows then you still have hope.
So I recommend to open a different post since your issue is different.
One try is to add acpi_osi="!Windows 2006" like mentioned in:
[https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

The BIOS usuially checks which is the OS booting and will not show all the feature if it is Linux.

---

