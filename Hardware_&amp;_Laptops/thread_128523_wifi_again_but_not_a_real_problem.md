---
title: "wifi again but not a real problem"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by slavik on 2006-02-11
once I install the windows drivers through ndisgtk for my broadcomm 4318, I can do **iwlist wlan0 scan** and it scans for networks and such. it also shows up in the graphical connection manager.

the trouble is that whenever I restart my system, my wifi card dissapepars from the connection manager. ndisgtk reports the drivers as being installed and to get the card back I have to uninstall the drivers and reinstall them. my settings are gone, too in this procedure.

another question is: instead of doin **iwlist wlan0 scan** is there a GUI front end that would scan for networks and allow me to connect to them? (does kismet work fine for this?)

---

### Post by moephan on 2006-02-11
In terms of your last question, I ended up writing such a utility in Python.

At some point soon I'll post it somewhere. In the meantime, if you'd like I can zip it all up and send it you if you want.

[IMG]http://ubuntuforum.org/attachment.php?attachmentid=6050&stc=1&d=1139709817[/IMG]

Cheers, Rick

---

### Post by slavik on 2006-02-11
HEY!!! THAT THING IS PERFECT!!!

give it to ubuntu devs so they can put it in dapper :D

btw, how difficult is it to create GUI in python?

---

### Post by moephan on 2006-02-11
As per our IM conversation, I zipped it up and attached it here. Let me know how it goes. Ping me if you need some help getting it going. I'd be happy to hear how it works if any one else gives it a try.

Cheers, Rick

---

### Post by moephan on 2006-02-11
Creating GUIs in Python is a piece of cake, and super fun. Search the web for the tutorial on pygtk.

Cheers, Rick

---

### Post by slavik on 2006-02-12
here's something else that bothers me. I have a button to enable/disable the wifi card. would be nice if I could use it. :) (it has a blue led under it which lights up when the wifi card drivers are installed.)

edit: your utility showed that no networks were available. I haven't done much testing but there should be 1 or 2 networks visible :) in my area.

---

### Post by batty505 on 2006-02-12
Hey folks,

I am having a problem trying to configure or install my wifi card driver?
I have downloaded the linksys 54G driver, installed ngtk, wine and updated breezy, and all others and still not able to install the linksys driver. Or atleast it dosent show it, under device manager?

I do notice there are broadcomm drivers for my wifi nic installed, but when I go to enable them from wireless drivers, I get a modem pcmcia.
And I dont see my SSID or anyone elses for that matter. There are plenty of open ports here... I would prefer to use mine but I cant even see mine! <sigh>

Ive googled and asked around here, and other linux forums, I've done wine, ngtk, updated my patches, from the wire, all I need left is to configure the wifi, and I should be MS free.

please help?
thanks
mike

---

### Post by moephan on 2006-02-12
Slavik,

Try clicking the refresh button. Also, make sure that you run it as sudo. If that doesn't work, would you mind sending me the output of an iwlist scan?
prompt$sudo iwlist scanning > iwlistoutput.txt

and then send me the file iwlistoutput.txt

Thanks.

I don't know how to enable your hardware switch. Sorry.

Cheers, Rick

---

### Post by batty505 on 2006-02-12
Hey Moephan,

I think slavik has his card working, just wants the bling stuff on his card to work.
Im the one who cant configure my wifi nic? I "hope" to be able to config the ssid, after the drivers get installed,  but just need to install the nic drivers in ubuntu.

Ive done ngtk and ndiswrapper, installed an updated both from the wire. Even installed wine? thought that i could run the exe from the home directory/folder

Ive tried to do automatix, but got hung up 1/2 way through the cmdline stuff.
Ive even done the custom location for driver? update? through the instructions here, but it didnt work.

please advise.
Mike

---

### Post by moephan on 2006-02-12
Mike,

I'm sorry you're having trouble configuring your wireless card. I would suggest starting a new post with the exact name of your wireless hardware in the title, which you can look up in the Applications->System Tools->System Information (hardware).   I'm not a wireless expert, but I have gotten wireless to work under multiple configurations, including ndiswrapper, so let me know when you repost and I'll take a look. Hopefully someone more expert then I am will see it too.

Cheers, Rick

---

### Post by batty505 on 2006-02-12
hey Rick

thanks again, I know its something I am doing wrong.
anyway, you got your stuff to work properly, your more up on me..

anyway, thanks I will do just that, and continue to see what linksys or anyone else has to say.

thanks again.

mike

---

