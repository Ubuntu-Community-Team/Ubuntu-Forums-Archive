---
title: "Printer setup ain't what it used to be"
date: 2021-04-21
forum: Hardware
---

### Post by sofasurfer on 2021-04-21
16.04 detected and setup my printer perfectly every time. Now with 20.04 its like the old days when you had to manually figure it all out. Am I missing something or what. In 16.04 I opened the dialog window, my printer was recognized by name and in a click or two I was printing. Now, however, I have to relearn what CUPS is all about and how to use it. Is there a shortcut here anywhere? I even reinstalled my OS with the printer turned on in the hope that it would be recognized and set up. By the way, its a HP officejet 3830. Can I by any chance install the print package from 16.04 and delete the one from 20.04?

---

### Post by brian_p on 2021-04-21
> Now, however, I have to relearn what CUPS is all about and how to use it. Is there a shortcut here anywhere? 

No shortcuts:

[https://wiki.debian.org/CUPSQuickPrintQueues](https://wiki.debian.org/CUPSQuickPrintQueues)

For the scanner:

[https://answers.launchpad.net/hplip/+question/690723](https://answers.launchpad.net/hplip/+question/690723)

---

### Post by ajgreeny on 2021-04-21
It's a long time since I had any problem with HP printers, in fact I don't think I ever have, and for the past several installations I have made of any of the *buntu family, our HP printer connected by wireless has been found with no action on my part.

It should be easy to find the printer whether USB or wireless connected, though it is important to give it a static IP address if using wireless.

If you continue to have problems try using the **hplip-gui** which you will need to install, which you may find easier than cups, though it should not be difficult using cups alone.

---

### Post by The Cog on 2021-04-21
Just a thought - maybe you have enabled a firewall that blocks the printer's announcements?
I have Ubuntu 20.04 and an HP envy just appears in my printers list. Mildly annoying is that if I rename it, another printer with the original name appears in the printers dialog within a minute or two. But I'll happily live with that.

---

### Post by brian_p on 2021-04-21
> **The Cog said:**
> Just a thought - maybe you have enabled a firewall that blocks the printer's announcements?
I have Ubuntu 20.04 and an HP envy just appears in my printers list. Mildly annoying is that if I rename it, another printer with the original name appears in the printers dialog within a minute or two. But I'll happily live with that.

It is not possible to change the name (destination) of an existing print queue. What the so-called renaming does is take the existing queue's attributes (URI etc) and create a second queue with the same attributes but a different name (destination). The first queue is then deleted.

However, you have cups-browsed on the system and it will auto-setup the first queue again. You do not need to live with this: ```
apt purge cups-browsed
```

---

### Post by cmcanulty on 2021-04-21
Have you installed HPLIP? It makes HP printer setup and management very easy

[https://developers.hp.com/hp-linux-imaging-and-printing]("https://developers.hp.com/hp-linux-imaging-and-printing")

---

### Post by ajgreeny on 2021-04-21
> **cmcanulty said:**
> Have you installed HPLIP? It makes HP printer setup and management very easy

[https://developers.hp.com/hp-linux-imaging-and-printing]("https://developers.hp.com/hp-linux-imaging-and-printing")
If you want a GUI for hplip, which is installed by default, I think, you need to install ***hplip-gui*** as I mentioned above.
If you are having problems finding the printer it is usually very simple with the HP-Toolbox that it provides, though you may have to enter the IP of the printer when trying to detect it.

---

### Post by sofasurfer on 2021-04-21
> **cmcanulty said:**
> Have you installed HPLIP? It makes HP printer setup and management very easy

[https://developers.hp.com/hp-linux-imaging-and-printing]("https://developers.hp.com/hp-linux-imaging-and-printing")

I do have hplip installed. I did NOT have hplip gui installed. I will try gui after I read the rest of the posts.

---

### Post by sofasurfer on 2021-04-21
> **ajgreeny said:**
> you may have to enter the IP of the printer when trying to detect it.

How do I find the printer IP?

---

### Post by sofasurfer on 2021-04-21
Here is exactly what I am able to do now.
Open a text document. Click 'print'. Error message says'could not start printer. Check printer configuration. I open printer dialog box and there is no printer. I click 'add printer'. It searches for printer and then says 'CUPS BRF PRINTER. I click 'ADD'. It says 'CUPS BRF PRINTER READY model Generic Text Only Printer'. I go back to my document and click 'print' and it says 'Could not start printer. Check your configuration'. I go back to the printer dialog box and click 'additional printer settings'. It shows 'CUPS BRF PRINTER'. I have no idea what to do after that.

---

### Post by brian_p on 2021-04-21
> **sofasurfer said:**
> I do have hplip installed. I did NOT have hplip gui installed. I will try gui after I read the rest of the posts.

When you have studied the rest of the posts, it would be good if you came to the following conclusions:

[LIST]
You have a modern printer that the printing system is designed to cater for.
[/LIST]
[list]
No part of HPLIP is needed. It is redundant. It may as well be removed from your system.
[/LIST]
[LIST]
Connecting the printer by wireless is the way forward and will automatically provide a printing service.
[/LIST]

---

### Post by ajgreeny on 2021-04-21
The printer setup should tell you somewhere what its IP address is, and you may also be able to find it in your router setup.
I usually set mine using the Reserved IP Addresses in my router setup, but that will depend very much on your router.

---

### Post by sofasurfer on 2021-04-21
I am connected by USB not wireless.
Why did my printer work effortlessly in 16.04 and then when 20.04 came out obviously the process was made less effective?

---

### Post by brian_p on 2021-04-21
> **sofasurfer said:**
> I am connected by USB not wireless.

So - set up a wireless connection to get you going. USB is doable, but I do not feel like doing it (unless my arm is twisted).
> 
Why did my printer work effortlessly in 16.04 and then when 20.04 came out obviously the process was made less effective?

Things change. The world moves on. Move on with it.

---

### Post by Dennis N on 2021-04-21
If you initially click on "Additional Printer Settings" instead of "Add" you can get the previous printer dialog. Maybe it will work better for you.

P.S.> Be sure the printer is turned ON.

---

### Post by sofasurfer on 2021-04-22
My printer now *APPEARS* to be functioning properly after running sudo hp-setup -i. I did read that it is required to have the newest hplip package but that hplip also depends on the newest python which apparently does not support ubuntu 20.04.

---

### Post by Autodave on 2021-04-22
Not a cure, but maybe worth posting since I ran into a similar problem.  Aunt's computer running 20.04 with an HP inkjet.  I installed 20.04 (previously had Win7 on it) and everything worked fine.  Printed test page: good.  Few days later she called and said it wouldn't print.  Went over and checked everything.  Tried new USB cable.  No go.  Removed HP-Lip and reinstalled.  Worked great.  Next week, same problem.  Removing and installing HP-LIP will make it print.  Rebooting the machine stops the printer from working until HP-LIP is removed and reinstalled.

---

### Post by sofasurfer on 2021-04-22
I was going to try that but did not. Now I guess I will since TODAY IT IS NOT WORKING AGAIN. I'm also going to start shopping for a new distro since printing is something I need very much. Manual printer configuration is something that I have never been able to accomplish and that is why I have always been so happy with 16.04. Not being a programmer I can not comprehend why when something work you would choose to downgrade its abilities. 
Thanks for your help and suggestions.

---

### Post by QIII on 2021-04-22
Strangely, the two HP printers I have in my home, both more recent than yours, both wireless, were detected quite without any effort on my part running 20.04.

The problem may indeed be USB, but not being there to investigate leaves us unable to say for sure.

As far as distro shopping, do as you wish.  That won't make anyone here suddenly admit to having an answer they have withheld from you and we won't beg you to stay,  Best of luck to you whichever distro you choose.

---

### Post by brian_p on 2021-04-23
> **QIII said:**
> Strangely, the two HP printers I have in my home, both more recent than yours, both wireless, were detected quite without any effort on my part running 20.04.

This is encouraging information and is precisely what the system is designed to do. However. sofasurfer seems determined not to follow the wireless route, in spite of needing printing  very much.

> The problem may indeed be USB, but not being there to investigate leaves us unable to say for sure.


Ubuntu introduced ippusbxd on 20.04. In general - it was a disaster. I would remove the package. This returns the printing system with USB to the state of 16.04.

---

