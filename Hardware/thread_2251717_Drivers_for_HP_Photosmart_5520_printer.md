---
title: "Drivers for HP Photosmart 5520 printer"
date: 2014-11-06
forum: Hardware
---

### Post by theHands on 2014-11-06
Hello all

I had to put in Ubuntu on this comp0uter as windowsw died.

Most things are working ok, but I can't get the printer to work.

I tried doing it with the menu and choosing my printer from the dropdown list, and it seemed to recognise it, but when I print a test page, absolutely nothing happens at all.

Maybe manually installing a driver would help?

Con somebody please explain how to run the downloaded file?

Its a HP photosmart 5520 printer

I tried this advice: [hplipopensource.com/hplip-web/gethplip.html]("http://hplipopensource.com/hplip-web/gethplip.html")

I drag the downloaded driver file onto my desktop, but the terminal comands wont work for me:

"ann@ann-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
ann@ann-desktop:~$ sh hplip-3.14.10.run
sh: 0: Can't open hplip-3.14.10.run
ann@ann-desktop:~$"

Can anyone please help as I'm totally stuck?

I'm not sure I understand why ubuntu cant just allow me to click the file with my mouse and simply install it that way?

Please can I have walkthrough that works on how to get this printer working, thanks very much.

---

### Post by tgalati4 on 2014-11-06
```
cd Desktop
```

All commands in linux are case sensitive.

```
sudo apt-get install hplip
```

Open a browser page:  [http://localhost:631](http://localhost:631)

Try installing the printer from the "Administration" tab.  Select the HP Photosmart 5520.  Print a test page, then print from an application.

---

### Post by theHands on 2014-11-06
I'm sorry, that local host website is extremely complicated
as is anything on Linux

I need a much clearer walkthrough please

I may have to just go back to windows.

The mind absolutely boggles how complicated linux can be..
I'm astounded and amazed time & time again

does it ever get any better?

---

### Post by MIJ-VI on 2014-11-07
> **theHands said:**
> Hello all

I had to put in Ubuntu on this comp0uter as windowsw died.

Most things are working ok, but I can't get the printer to work.

I tried doing it with the menu and choosing my printer from the dropdown list, and it seemed to recognise it, but when I print a test page, absolutely nothing happens at all.

Maybe manually installing a driver would help?

Con somebody please explain how to run the downloaded file?

Its a HP photosmart 5520 printer

I tried this advice: [hplipopensource.com/hplip-web/gethplip.html]("http://hplipopensource.com/hplip-web/gethplip.html")

I drag the downloaded driver file onto my desktop, but the terminal comands wont work for me:

"ann@ann-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
ann@ann-desktop:~$ sh hplip-3.14.10.run
sh: 0: Can't open hplip-3.14.10.run
ann@ann-desktop:~$"

Can anyone please help as I'm totally stuck?

I'm not sure I understand why ubuntu cant just allow me to click the file with my mouse and simply install it that way?

Please can I have walkthrough that works on how to get this printer working, thanks very much.

After reading your post here's what I did:

1) I downloaded *hplip-3.14.10.run* (but I didn't bother downloading the digital certificate).
2) I opened a Terminal window.
3) I dragged *hplip-3.14.10.run* into the Terminal window.
4) I tapped the <Enter> key.
5) *hplip-3.14.10.run* then appeared ready to walk me through its installation (but I went no further since I don't have a printer).

---

### Post by tgalati4 on 2014-11-07
Yes, linux is complicated.  It takes 10 years to get good at it.  

The Photosmart 5520 printer is in the current version of *hplip*.  You don't need the latest one.

Run the command I suggested in Post #2 then run:

```
hp-toolbox
```

---

### Post by theHands on 2014-11-08
> **MIJ-VI said:**
> After reading your post here's what I did:

1) I downloaded *hplip-3.14.10.run* (but I didn't bother downloading the digital certificate).
2) I opened a Terminal window.
3) I dragged *hplip-3.14.10.run* into the Terminal window.
4) I tapped the <Enter> key.
5) *hplip-3.14.10.run* then appeared ready to walk me through its installation (but I went no further since I don't have a printer).

I tried and this happened:


ann@ann-desktop:~/Desktop$ '/home/ann/Desktop/hplip-3.14.10.run' 
bash: /home/ann/Desktop/hplip-3.14.10.run: Permission denied
ann@ann-desktop:~/Desktop$

---

### Post by theHands on 2014-11-08
> **tgalati4 said:**
> Yes, linux is complicated.  It takes 10 years to get good at it.  

The Photosmart 5520 printer is in the current version of *hplip*.  You don't need the latest one.

Run the command I suggested in Post #2 then run:

```
hp-toolbox
```

I managed to install ot then run it, but it wont pick up my printer
It says there are no devices recognised

I simply don't have time to mess around with this OS anymore

I'm putting windows back in because it works

Thanks for the help, but it's just one problem after another with linux

---

### Post by tgalati4 on 2014-11-08
It's possible that the 5520 doesn't communicate its status.  

With the printer plugged in and connected to the computer via USB.  Open the Control Center (Control Panel) and bring up the Printers dialog and hit the + (Add) button.  It should show up in a list of connected printers.  Then try printing a test page.

Yes, linux requires some tweaking to get everything working.  But once it works, you will feel better about it.

Everything is fixable.  Patience is key.

---

### Post by MIJ-VI on 2014-11-08
> **theHands said:**
> I tried and this happened:


ann@ann-desktop:~/Desktop$ '/home/ann/Desktop/hplip-3.14.10.run' 
bash: /home/ann/Desktop/hplip-3.14.10.run: Permission denied
ann@ann-desktop:~/Desktop$

1) Right-click on *hplip-3.14.10.run* and from the pop-up menu select 'Properties'-->'Permissions' and then enable 'Allow executing file as program' and then close the pop-up menu.
2) At this point you can double-click on *hplip-3.14.10.run*, and from the resulting dialogue box, click the 'Run' button.

---

### Post by theHands on 2014-11-14
Thanks for the advice
I installed windows again instead.

I'd still consider using Linux as a fast and neat internet browsing option; beyond that, it seems far to much trouble to do anything with (even printing).
I use Skype often also, and for some reason, Skype on Linux is very bad.

Thanks

---

### Post by MIJ-VI on 2014-11-14
If you wish to use GNU/Linux for Internet browsing then it can be run from within [https://www.virtualbox.org/](https://www.virtualbox.org/)

An Ubuntu 14.04.1 LTS derivative which is also supported until April, 2019 and that comes with all of the multimedia codecs one needs along with a lighter, more Windows-like UI:

Linux Mint 17 "Qiana" - MATE (64-bit) - Linux Mint
[http://www.linuxmint.com/edition.php?id=160](http://www.linuxmint.com/edition.php?id=160)

---

### Post by theHands on 2014-11-14
> **MIJ-VI said:**
> If you wish to use GNU/Linux for Internet browsing then it can be run from within [https://www.virtualbox.org/](https://www.virtualbox.org/)

An Ubuntu 14.04.1 LTS derivative which is also supported until April, 2019 and that comes with all of the multimedia codecs one needs along with a lighter, more Windows-like UI:

Linux Mint 17 "Qiana" - MATE (64-bit) - Linux Mint
[http://www.linuxmint.com/edition.php?id=160](http://www.linuxmint.com/edition.php?id=160)


Sorry, I'm not sure what your getting at.

You recommend Linux mint 17, running in a virtually inside a windows OS?

---

### Post by MIJ-VI on 2014-11-14
> **theHands said:**
> Sorry, I'm not sure what your getting at.

You recommend Linux mint 17, running in a virtually inside a windows OS?

If you wish to browse the web via a GNU/Linux distro in order to exploit its lower vulnerability to malware compared to Windows, then the least messy way of doing so is to run it from within a (free) virtual machine like VirtualBox.

I suggested Linux Mint 17 MATE because MATE runs faster than Ubuntu's UNITY and its User Interface is familiar to anyone who has used Windows 2000, XP or 7.

How to use VirtualBox in Windows 7 at DuckDuckGo
[https://duckduckgo.com/?q=How+to+use+VirtualBox+in+Windows+7](https://duckduckgo.com/?q=How+to+use+VirtualBox+in+Windows+7)

---

### Post by theHands on 2014-11-15
> **MIJ-VI said:**
> If you wish to browse the web via a GNU/Linux distro in order to exploit its lower vulnerability to malware compared to Windows, then the least messy way of doing so is to run it from within a (free) virtual machine like VirtualBox.

I suggested Linux Mint 17 MATE because MATE runs faster than Ubuntu's UNITY and its User Interface is familiar to anyone who has used Windows 2000, XP or 7.

How to use VirtualBox in Windows 7 at DuckDuckGo
[https://duckduckgo.com/?q=How+to+use+VirtualBox+in+Windows+7](https://duckduckgo.com/?q=How+to+use+VirtualBox+in+Windows+7)

Thanks
that sounds intersting

---

### Post by theHands on 2014-11-15
It didnt work

I just get a blank linux mint logo screen in the virtual box
with no options or anything.

Now there is ZERO need for me to use linux because even this wont run well.
I followed a youtube tutorial and it didn't work.
I refuse to spend anymore time with this system.
Sorry if that sounds harsh, but its just too much trouble.
Thanks for the suggestions though

---

### Post by MIJ-VI on 2014-11-15
In the interest of helping others who may be using the same PC, what is the exact make and model # of your machine?

---

### Post by theHands on 2014-11-18
Hi
Sure, It's a Samsung Np355v5c
Thats the model I was just using when trying the virtual box.


As for the printer problem, that was a different computer with a foxconn A88gmv series Motherboard, I don't know that much more about it as it's not in front of me anymore.
Good luck!

---

### Post by MIJ-VI on 2014-11-19
Thank you.

---

### Post by MIJ-VI on 2014-11-19
> **theHands said:**
> Hi
Sure, It's a **Samsung** Np355v5c
Thats the model I was just using when trying the virtual box.


As for the printer problem, that was a different computer with a foxconn A88gmv series Motherboard, I don't know that much more about it as it's not in front of me anymore.
Good luck!

You may wish to read this:

It seems that installing GNU/Linux or Windows in UEFI mode can brick some Samsung laptops.

installation - Can i install Ubuntu 13.04 on a Samsung NP355V5C (Windows 8 preinstalled) laptop? - Ask Ubuntu
[http://askubuntu.com/questions/335504/can-i-install-ubuntu-13-04-on-a-samsung-np355v5c-windows-8-preinstalled-laptop](http://askubuntu.com/questions/335504/can-i-install-ubuntu-13-04-on-a-samsung-np355v5c-windows-8-preinstalled-laptop)

NP355V5C (NP355V5C-A03CA) | Support | SAMSUNG Canada
[https://www.samsung.com/ca/support/model/NP355V5C-A03CA](https://www.samsung.com/ca/support/model/NP355V5C-A03CA)

--

Foxconn PRODUCT : Motherboard : Details (A88GMV)
[http://www.foxconnchannel.com/ProductDetail.aspx?T=motherboard&U=en-us0000504](http://www.foxconnchannel.com/ProductDetail.aspx?T=motherboard&U=en-us0000504)

---

### Post by miguelangel2 on 2015-07-08
Hi,

Here's how I solved it. My printer is an HP Photosmart 5520. I'm using it in a wireless connection. Didn't need to wire it to the laptop for the first configuration either.

1) From your printer's screen click on the wireless connection icon to see the IP, MAC address, network, etc. Take note of the IP address. You'll need it.

2) Open up a terminal window as suggested by @tgalati4 and...

     sudo apt-get install hplip
     hp-toolbox

3) The last command brings up the HP-Manager window. Then choose...

     "Set up device" > "Network/Ethernet/Wireless network (Direct connection or JetDirect" > "Manual discovery" > "IP address or network name:" *Your printer's IP address*.

[IMG]https://www.evernote.com/shard/s94/res/1073aadb-6ebc-4726-b9a1-0c2978999d60/Screenshot%20from%202015-07-08%2014%3A08%3A22.png?search=printer&resizeSmall&width=741[/IMG]

4) Click next, choose your printer from the list of printers found and finish.

Done. Happy printing.
Hope this helps others.

---

