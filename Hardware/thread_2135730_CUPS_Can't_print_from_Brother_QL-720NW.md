---
title: "CUPS: Can't print from Brother QL-720NW"
date: 2013-04-15
forum: Hardware
---

### Post by simenschi on 2013-04-15
Hi! I'm trying to get my Brother QL-720NW WIFI label printer to work from my Ubuntu server. So far I've installed the necessary LPR and cupswrapper drivers, following [Brothers own linux guide]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_esp1.html"). The printer shows up successfully on the CUPS web interface, and I've set the default media sizes to fit the label the printer uses(which came up as default). Here's my **lpstat -tl:**

```
$ lpstat -tl
scheduler is running
system default destination: Brother_QL-720NW
device for Brother_QL-720NW: socket://192.168.1.166
Brother_QL-720NW accepting requests since Mon 15 Apr 2013 12:52:35 PM CEST
printer Brother_QL-720NW is idle.  enabled since Mon 15 Apr 2013 12:52:35 PM CEST

```

So, when I'm trying to send a sample file to the printer with **lp test.txt **it says:
```
$ lp test.txt
request id is Brother_QL-720NW-17 (1 file(s))

```

But no response from the printer at this point. The printer has a simple web interface(cant find any logs there though...) which simply says "READY". Here is my [**error_log from cups when starting cups**]("http://pastebin.com/2vaCC0mv"), which i think looks fine..?

[**And here's the log from when I'm trying to print the sample file.**]("http://pastebin.com/dcN0MafN")

That looks OK doesn't it..? Like i said, the printer itself gives me no feedback, no flashing light, nothing. 

I'm not really sure where to go from here, so does anyone have any idea what might be wrong or how I can troubleshoot any further?

---

### Post by pdc on 2013-04-15
is there anything here of value to you?

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by simenschi on 2013-04-23
I'm afraid not @pdc...

Today I tried starting from scratch and this is what I've done so far:

[COLOR=#000000][FONT=Arial]First I installed CUPS and [LPR and cupswrapper drivers from Brothers website]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html"), and now my QL-720NW shows up in the CUPS web interface. I set the default media size to fit my label(29x90mm). I clicked "Test print page" on the QL-720NW and it says *"Sending data to printer."* a few seconds, and then disappears and changing state to *Idle, Accepting Jobs, Not Shared, Server Default*. But my printer does nothing, not even a led light blinking.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]My cups/error_log looks like this. I have googled the *AddProfile failed* error, and found someone suggesting it is a bug in Ubuntu 12.10, but I've also read that Arch users have had the same error, so I'm not sure. And the [Uknown directive SystemGroup error is just a harmless error according to this site.]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1088448")

[/FONT][/COLOR]> E [23/Apr/2013:12:20:47 +0200] Unknown directive SystemGroup on line 18 of /etc/cups/cupsd.conf.
W [23/Apr/2013:12:20:47 +0200] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_QL_720NW

When I run **lpstat -tl** after trying to print a test page or a text file using **lp test.txt**, it says it's sending data to the printer. But the printer does nothing.

> # lpstat -tl
scheduler is running
system default destination: QL-720NW
device for QL-720NW: usb://Brother/QL-720NW?serial=000K2Z658058
QL-720NW accepting requests since Tue 23 Apr 2013 12:45:56 PM CEST
printer QL-720NW is idle.  enabled since Tue 23 Apr 2013 12:45:56 PM CEST
    Sending data to printer.


Any suggestions?

---

### Post by simenschi on 2013-05-26
Found a solution to my problem, p[osted on stackoverflow]("http://stackoverflow.com/questions/16164974/brother-ql-720nw-printing-labels-using-cups-ubuntu").

Quoted from stackoverflow:
> [COLOR=#000000][FONT=Arial]I finally got it to print on my Ubuntu system. The problem seemed to be that the drivers from Brother is not 64bit compatible, and I was using a 64bit version of Ubuntu.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]I tried on Debian first, after learning from @sampi that he got it to work on Debian. When installing the drivers I got an error message, which I didn't get on Ubuntu, suggesting a 32/64bit issue. So after installing the ia32-libs packages it worked on Debian. I then tried installing a 32bit version of Ubuntu on my server, and now the printer did work.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]But I can only get the printer to work through wifi(both on Debian and Ubuntu). No success with the USB cable, but that's not an issue for me.[/FONT][/COLOR]

---

