---
title: "3 in 1 printer"
date: 2017-06-19
forum: Hardware
---

### Post by ehud2 on 2017-06-19
I'm just looking for opinions. What is the easiest to install and best working 3 in 1 printer you have come across? I'm running xubuntu 17.04. It's for a small church that doesn't really need to print much. Thanks.

---

### Post by Autodave on 2017-06-19
Personally, I find HP to be the easiest. Scanning can sometimes be a challenge though: I use the USB port and scan to a thumb drive.  I have also heard that Brothers are esay to set up, but I have no experience with Them. Canon (which I do have experience with) is terrible (in my opinion: just too much work and never ever get it quite right). I have heard horror stories about Epson, too.

---

### Post by ehud2 on 2017-06-19
Thanks Autodave. I appreciate the input.

---

### Post by pdc on 2017-06-19
Hi there ehud; ..... well this type of question often appears; a chance for one to sing about one's favourites; 

...... have you thought if you want colour; ............ inkjet; ........       a laser ............ 

I find that Canon's printers are needing very little forum support these days; **ie they work just FINE!!**     their inkjets all use the same driver now; it runs them all; so folks maybe ask on a forum where to get a driver; but pointed to a driver site; then all is good; so facts are: Canon works fine

ironically, it is HP that are providing the most frequently mentioned printers providing troubles; on the ubuntu and Mint forums I feel; eg browse the Mint forum [https://forums.linuxmint.com/;](https://forums.linuxmint.com/;) ........any HP enthusiasts are welcome to join the forums and support those having troubles with HP;

other makes: Brother provide an installer script; (as does Canon): so when you run the installer script, it should do all the work for you; if you go for a multi-function device; (ie printer and scanner), I find the Canon scanner works well; installing a Brother scanner driver can give problems; 

Epson just provide the drivers; (no script to register the printer); and the driver is just their generic one; so some folks comment on the low dpi they seem to get; their scanner needs software tweaking to get it to work;

If one wants a black only laser; (also called mono); then folks like Samsung make cheap and very effective lasers; and they go for ever without needing new ink cartridges; perhaps fitting your situation of the church not doing much printing; another option is a second-hand printer; or from within the ranks of the congregation, some kindly soul may well have a little used printer they would happily donate; the forums can offer support from there; but come ubuntu 17.04, printer recognition will be even better I suspect: ie plug and the system does the set up for you ..

---

### Post by ehud2 on 2017-06-21
Thank you pdc. I appreciate the input. I'm not sure what direction I'm going to head, but I think I'll do a little more digging now. Probably would have dove into the HP.

---

### Post by vocx on 2017-06-21
> **ehud2 said:**
> Thank you pdc. I appreciate the input. I'm not sure what direction I'm going to head, but I think I'll do a little more digging now. Probably would have dove into the HP.
I also recommend HP. From the days of Ubuntu 6.04 I always heard HP had good support in Linux. Now it seems to be even better.

HP has the HPLIP project to support their devices
[LIST]
[*][http://hplipopensource.com/hplip-web/about.html](http://hplipopensource.com/hplip-web/about.html)
[*][http://hplipopensource.com/hplip-web/recommended.html](http://hplipopensource.com/hplip-web/recommended.html)
[*][http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html)
[/LIST]

It's included in most recent distributions
```

sudo apt install hplip

```

Once you have your HP printer connected either by USB, by Ethernet cable, or by Wi-Fi, you can issue
```

hp-setup

```
to proceed to the configuration. With a graphical user interface, I think it's as user-friendly as it can be in Linux.

I currently have the HP-LaserJet Pro MFP m127fn printer-scanner-fax-copier connected to my local network, and it works fine. I can print and scan remotely from Linux and Windows computers. I should have bought the wireless version, but I didn't notice and bought the wired version.

For scanning I use the Ubuntu "simple-scan" tool. It's enough for my needs.
```

sudo apt install simple-scan
simple-scan

```

It also has a one-button copy function. No need to turn on any computer. Just turn on the printer, place your sheet, press copy. Excellent to produce copies of fliers, exams, certificates, and other documents.

I don't work for HP, but I feel compelled to support brands that play well with Linux.

I don't have much experience with Canon, Epson, or Samsung. They mostly make cheap ink-jet color printers. They don't have as good Linux support, and you have to buy ink cartridges constantly. Go for a laser printer, and for the Wi-Fi version whenever you can for a cable-free experience.

For years I had an old Brother laser printer, but never used it with Linux. I have read they are extremely reliable but haven't actually used one recently.

---

### Post by him610 on 2017-06-22
Hello ehud2,

From #4, > ...... have you thought if you want colour; ............ inkjet; ........ a laser ............ 


Good question. What do you want your printer to do? What are your needs? Define your requirements. 

If only going to be used for occasional small jobs, consider a laser printer. Inkjet cartridges tend to dry out, and they are more expensive. 

Do you intend to print from only one computer, or more? 

Do you want to be capable of have expanded access to the printer?

The use of the printer will expand over time.   

If you don't need color, don't get it.

I have a Dell 1700N laser printer that I have owned for over 10 years. Dell has not provided driver software since for two Windows releases. I have been able to use it continuously with each upgrade, new release of Ubuntu ever since I purchased it.

I also own a Brother MFC 7360N multifunction laser printer that I bought ($100) refurbished from Staples a couple of years ago. Brother has the Linux drivers on its website. I have experienced NO issues configuring the MFC 7360N to print, scan, copy, or fax from any one of several computers.  Some people report issues; your mileage may vary.

---

