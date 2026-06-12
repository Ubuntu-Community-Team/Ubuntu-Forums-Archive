---
title: "Brother Printer MFC-J430W Stopped Printing Wirelessly"
date: 2022-02-15
forum: Hardware
---

### Post by jduff on 2022-02-15
Very odd, after a recent update my Brother Printer MFC-J430W Stopped Printing Wirelessly.

It's been working great for a few years now printing and scanning but yesterday it just stopped. Upgrade change something?

I can print via USB but it would be great to get the wireless function back.

If you know of any new changes or issues with Ubuntu that would cause that and a fix it would be great to hear of it.

Thanks.

---

### Post by SeijiSensei on 2022-02-15
Have you considered wiring the printer directly to your router with an Ethernet cable? Then every device on your network can see it including both wireless and wired devices. The Brother app (iPrint&Scan) for my Android phone sees and uses the printer via this method. The printer has wifi capability, but I don't use it.

---

### Post by brian_p on 2022-02-15
What distro did you upgrade?

Let's see the state of the wireless connection and the printer. Give

```
avahi-browse -rt _ipp._tcp 
``` ```
avahi-browse -rt _uscan._tcp 
``` ```
driverless
```

---

### Post by jduff on 2022-02-15
There is no ethernet port, it's either USB or wireless for a connection.

I'm seeing other people who are having a similar issue in updated Ubuntu OSes for this printer.

Thank you for the help.

---

### Post by jduff on 2022-02-15
Here are the replies I got in terminal:

$ avahi-browse -rt _ipp._tcp
+ enp4s0 IPv4 Brother MFC-J430W                             Internet Printer     local
= enp4s0 IPv4 Brother MFC-J430W                             Internet Printer     local
   hostname = [BRN008092A00B71.local]
   address = [192.168.42.80]
   port = [631]
   txt = ["UUID=e3248000-80ce-11db-8000-008092a00b71" "URF=SRGB24,W8,CP1,IS1-7,MT1-8-11,OB0,PQ4,RS300,OFU0" "TBCP=F" "Transparent=T" "Binary=T" "PaperCustom=T" "Scan=T" "Duplex=F" "Copies=F" "Color=T" "usb_CMD=HBP,BRPJL,URF" "usb_MDL=MFC-J430W" "usb_MFG=Brother" "priority=25" "adminurl=http://BRN008092A00B71.local./net/net/airprint.html" "product=(Brother MFC-J430W)" "ty=Brother MFC-J430W" "note=" "rp=ipp/port1" "pdl=image/urf,application/octet-stream,application/vnd.brother-hbp" "qtotal=1" "txtvers=1"]

$ avahi-browse -rt _uscan._tcp
there was no response, it returns to an empty line

$ driverless
ipp://BRN008092A00B71.local:631/ipp/port1

---

### Post by brian_p on 2022-02-16
The wireless connection looks Ok. Try setting up a manual queue.

```
lpadmin -p j430 -v "ipp://BRN008092A00B71.local:631/ipp/port1" -E -m everywhere
```

Test with ```
lp -d j430 /etc/nsswitch.conf
```

---

### Post by mIk3_08 on 2022-02-16
> **jduff said:**
> Very odd, after a recent update my Brother Printer MFC-J430W Stopped Printing Wirelessly.
It's been working great for a few years now printing and scanning but yesterday it just stopped. Upgrade change something?
I can print via USB but it would be great to get the wireless function back.
If you know of any new changes or issues with Ubuntu that would cause that and a fix it would be great to hear of it.
Thanks. Thus your printer already connected to your network or router directly? If it did, you can easily find it to your Linux Ubuntu Operating System so you can locally scan and add it to your Linux Ubuntu Operating System via network. good luck and cheers.

---

### Post by mIk3_08 on 2022-02-16
> **jduff said:**
> There is no ethernet port, it's either USB or wireless for a connection.
I'm seeing other people who are having a similar issue in updated Ubuntu OSes for this printer.
Thank you for the help.
Connect your printer directly to your router wirelessly so you will be able to see and add it to your Linux Ubuntu Operating System.
It could be best if you could install the brother printer driver coming from the brother website. Just follow the instruction then.
Good Luck and Cheers.

---

### Post by SeijiSensei on 2022-02-16
> **jduff said:**
> There is no ethernet port, it's either USB or wireless for a connection.
That's truly unfortunate.

---

### Post by mIk3_08 on 2022-02-17
> **jduff said:**
> There is no ethernet port, it's either USB or wireless for a connection.
If the printer/scanner doesn't have this ethernet and can able to connect via wireless then connect it directly to your router wirelessly once its connected successfully then
connect also your Linux Ubuntu machine (Desktop Personal Computer) to the same router where your printer/scanner is connected with. When all is successfully connected to the same router,
try to add/scan with your Linux Ubuntu machine (Desktop Personal Computer) to find out if your printer/scanner can be detected with your Linux Ubuntu machine (Desktop Personal Computer). 
Once detected, then add your printer/scanner using your Linux Ubuntu machine (Desktop Personal Computer). So good Luck and Cheers.

---

