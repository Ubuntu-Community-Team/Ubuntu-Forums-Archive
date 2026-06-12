---
title: "Brother Laser Printer HL-L2340DW, wifi"
date: 2020-05-31
forum: Hardware
---

### Post by mawil10132 on 2020-05-31
Brother Laser Printer HL-L2340DW,  on Dell Inspirion P75F

Trying to connect to printer via WiFi.  Can't find Linux ( even though links appear. ) drivers through Brother.

---

### Post by kurt18947 on 2020-05-31
Have you seen this?

[https://support.brother.com/g/b/faqend.aspx?c=eu_ot&lang=en&prod=mfcl2700dw_us_eu_as&faqid=faq00100429_000](https://support.brother.com/g/b/faqend.aspx?c=eu_ot&lang=en&prod=mfcl2700dw_us_eu_as&faqid=faq00100429_000)

I mostly use ethernet connections, my only wifi effort was with a machine with a keypad which made it simple to enter the wifi password. Brother also has an online networking manual which goes into more detail about complex network setups. I don't know where to find that networking info quickly but it was around in the support section. Once you get on the wifi network connected the printer should work. I recommend the package "system-config-printer". If your distro doesn't have it (many do) it's available in the repositories,  I find that app more informative than what comes by default in Ubuntu(gnome). You can open it either from a terminal or alt-F2 then type the name.

---

### Post by SeijiSensei on 2020-06-01
I strongly suggest hard wiring the printer to your router with an Ethernet cable.  Then give it a static IP address within your network subnet.

---

### Post by mawil10132 on 2020-06-02
> **kurt18947 said:**
> Have you seen this?

[https://support.brother.com/g/b/faqend.aspx?c=eu_ot&lang=en&prod=mfcl2700dw_us_eu_as&faqid=faq00100429_000](https://support.brother.com/g/b/faqend.aspx?c=eu_ot&lang=en&prod=mfcl2700dw_us_eu_as&faqid=faq00100429_000)

I mostly use ethernet connections, my only wifi effort was with a machine with a keypad which made it simple to enter the wifi password. Brother also has an online networking manual which goes into more detail about complex network setups. I don't know where to find that networking info quickly but it was around in the support section. Once you get on the wifi network connected the printer should work. I recommend the package "system-config-printer". If your distro doesn't have it (many do) it's available in the repositories,  I find that app more informative than what comes by default in Ubuntu(gnome). You can open it either from a terminal or alt-F2 then type the name.

I've performed WiFi setup already but on my Win10 laptop, which Brother provides drivers and all for.   I seems the problem is reversed in that I need ubuntu to fond the printer already connected to WiFi.

---

### Post by mawil10132 on 2020-06-02
> **SeijiSensei said:**
> I strongly suggest hard wiring the printer to your router with an Ethernet cable.  Then give it a static IP address within your network subnet.

Don't have ethernet in the back room where printer is staged.

---

### Post by SeijiSensei on 2020-06-03
Point a browser on the Linux client to the address [http://localhost:631/](http://localhost:631/).  What does the "add a printer" routine show?

---

### Post by slickymaster on 2020-06-03
*Thread moved to **Hardware**.*

---

### Post by mawil10132 on 2020-06-03
> **SeijiSensei said:**
> Point a browser on the Linux client to the address [http://localhost:631/](http://localhost:631/).  What does the "add a printer" routine show?


I see my printer.

    [TABLE="class: list"]
[TR]
[TH]Queue Name[/TH]
[TH]Description[/TH]
[TH]Location[/TH]
[TH]Make and Model[/TH]
[TH]Status[/TH]
[/TR]
[TR]
[TD][HL-L2340D-series]("http://localhost:631/printers/HL-L2340D-series")[/TD]
[TD]Brother HL-L2340D series[/TD]
[TD]mawil1013-Inspiron-5575[/TD]
[TD]Brother HL-L2340D series, using brlaser v6[/TD]
[TD]Idle[/TD]
[/TR]
[/TABLE]

---

### Post by brian_p on 2020-06-03
> I see my printer.

Your initial post gave the impression you could not connect to your network with wireless. That obstacle seems to have been overcome. Good.

Now give the outputs of ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
``` ```
driverless
```

---

### Post by mawil10132 on 2020-06-03
Driving right now, l'll reply in one hour!! Thanks

---

### Post by mawil10132 on 2020-06-03
> **brian_p said:**
> Your initial post gave the impression you could not connect to your network with wireless. That obstacle seems to have been overcome. Good.

Now give the outputs of ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
``` ```
driverless
```

 Here's everything as it appeared on command lines;

mawil1013@mawil1013-Inspiron-5575:~$ avahi-browse -rt _ipp._tcp
+ wlp2s0 IPv4 Brother HL-L2340D series                      Internet Printer     local
= wlp2s0 IPv4 Brother HL-L2340D series                      Internet Printer     local
   hostname = [BRWD46A6A7561F9.local]
   address = [192.168.1.84]
   port = [631]
   txt = ["print_wfds=T" "UUID=e3248000-80ce-11db-8000-d46a6a7561f9" "PaperMax=legal-A4" "kind=document,envelope,label" "URF=W8,CP1,IS4-1,MT1-3-4-5-8,OB10,PQ4,RS300-600,V1.3,DM1" "TBCP=F" "Transparent=T" "Binary=T" "PaperCustom=T" "Scan=F" "Fax=F" "Duplex=T" "Copies=T" "Color=F" "usb_CMD=PJL,HBP,URF" "usb_MDL=HL-L2340D series" "usb_MFG=Brother" "priority=25" "adminurl=http://BRWD46A6A7561F9.local./net/net/airprint.html" "product=(Brother HL-L2340D series)" "ty=Brother HL-L2340D series" "note=" "rp=ipp/print" "pdl=application/octet-stream,image/urf,image/pwg-raster" "qtotal=1" "txtvers=1"]
mawil1013@mawil1013-Inspiron-5575:~$ avahi-browse -rt _uscan._tcp
mawil1013@mawil1013-Inspiron-5575:~$ avahi-browse -rt _uscan._tcp
mawil1013@mawil1013-Inspiron-5575:~$ driverless
ipp://Brother%20HL-L2340D%20series._ipp._tcp.local/

---

### Post by brian_p on 2020-06-04
> mawil1013@mawil1013-Inspiron-5575:~$ driverless
ipp://Brother%20HL-L2340D%20series._ipp._tcp.local/

This output is a URI. Execute ```
lpadmin -p PRINT_Q_NAME -v URI -m everywhere
``` PRINT_Q_NAME may be anything you choose. URI is the output of the *driverless* command. Test printing to the queue with ```
lp -d PRINT_Q_NAME /etc/nsswitch.conf
```

How's that?

---

### Post by mIk3_08 on 2020-06-04
you can also try this command, mawil10132:
```
lp -dBrother HL-L2340D .profile
```

---

### Post by SeijiSensei on 2020-06-04
> **mawil10132 said:**
> I see my printer.
Good.  You should be able to make it the default by using the administrative tools available through the web interface.

If you have problems finding a driver, you should run the Brother Install Tool for this printer: [https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2340dw_us_eu_as&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2340dw_us_eu_as&os=128)

---

### Post by mawil10132 on 2020-06-06
> **brian_p said:**
> This output is a URI. Execute ```
lpadmin -p PRINT_Q_NAME -v URI -m everywhere
``` PRINT_Q_NAME may be anything you choose. URI is the output of the *driverless* command. Test printing to the queue with ```
lp -d PRINT_Q_NAME /etc/nsswitch.conf
```

How's that?

mawil1013@mawil1013-Inspiron-5575:~$ lpadmin -p PRINT_Q_NAME -v URI -m everywhere
lpadmin: Bad printer URI "URI".
mawil1013@mawil1013-Inspiron-5575:~$ lp -d PRINT_Q_NAME /etc/nsswitch.conf
lp: No such file or directory
mawil1013@mawil1013-Inspiron-5575:~$

---

### Post by mawil10132 on 2020-06-06
> **SeijiSensei said:**
> Good.  You should be able to make it the default by using the administrative tools available through the web interface.

If you have problems finding a driver, you should run the Brother Install Tool for this printer: [https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2340dw_us_eu_as&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2340dw_us_eu_as&os=128)


mawil1013@mawil1013-Inspiron-5575:~$ cd downloads
bash: cd: downloads: No such file or directory
mawil1013@mawil1013-Inspiron-5575:~$ cd home
bash: cd: home: No such file or directory
mawil1013@mawil1013-Inspiron-5575:~$ CD downloads
CD: command not found
mawil1013@mawil1013-Inspiron-5575:~$ gunzip linux-brprinter-installer-*.*.*-*.gz
gzip: linux-brprinter-installer-*.*.*-*.gz: No such file or directory
mawil1013@mawil1013-Inspiron-5575:~$ cd downloads 
bash: cd: downloads: No such file or directory
mawil1013@mawil1013-Inspiron-5575:~$ gunzip linux-brprinter-installer-2.1.1-1.gz
gzip: linux-brprinter-installer-2.1.1-1.gz: No such file or directory
mawil1013@mawil1013-Inspiron-5575:~$ cd downloads gunzip linux-brprinter-installer-2.1.1-1.gz
bash: cd: too many arguments

---

### Post by oldfred on 2020-06-06
do ll or ls -l 
# that is el not 1 nor cap I (eye) to see list of files & folder in /home.

You should see that Downloads folder has a cap D. In Linux case is important.

---

### Post by CelticWarrior on 2020-06-06
Linux/Unix is case sensitive.

Start with ```
cd Downloads
```
You should be able to figure out the rest from there.

---

### Post by brian_p on 2020-06-06
> **mawil10132 said:**
> mawil1013@mawil1013-Inspiron-5575:~$ lpadmin -p PRINT_Q_NAME -v URI -m everywhere
lpadmin: Bad printer URI "URI".
mawil1013@mawil1013-Inspiron-5575:~$ lp -d PRINT_Q_NAME /etc/nsswitch.conf
lp: No such file or directory
mawil1013@mawil1013-Inspiron-5575:~$


As was indicated, PRINT_Q_NAME and URI are placeholders. You do not type them as you have done. Please read what I wrote, particularly regarding what is substituted for URI. You can substitute whatever you want for PRINT_Q_NAME - but not for URI.

---

### Post by brian_p on 2020-06-06
> If you have problems finding a driver, you should run the Brother Install Tool for this printer: 

This is a modern printer. Vendor drivers are completely unnecessary. But users love their drivers and still recommend them after having two years of driverless printing on Ubuntu. Progress retarded.

---

### Post by SeijiSensei on 2020-06-06
In general, I agree entirely. I offered the Printer Tool as a last resort. It works quite well, especially on 3-in-1 devices with a scanner.

I have my HL-3170CDW set to use Postscript which is the only way I can print envelopes correctly.

---

