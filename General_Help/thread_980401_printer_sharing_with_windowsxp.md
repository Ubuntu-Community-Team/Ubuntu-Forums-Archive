---
title: "printer sharing with windowsxp"
date: 2008-11-12
forum: General Help
---

### Post by caymahallesi on 2008-11-12
Hi guys
I have ubuntu 8.10 that has direct connected hp 2175 usb printer. I like to let my wife print from laptop (wireless) to this printer. 

I searched internet and found out about samba. I installed it and from my windows xp I was able to see this machine as server , but when I double click on it from my windows xp machine I get a prompt for username and password. I gave up yesterday and tried again tonight. 

Tonight I can't see the same server (ubuntu) from my windows xp anymore. I reinstalled the samba didn't help. I even tried installing/configuring cups. Neither helped. 

I also enabled the sharing from  system>administration>printing
still ubuntu machine won't showup on windowsxp network neighbours list. 

I need some help.

please send me some info. 

thanks

[COLOR="Red"]p.s. just know I checked [http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/) tutorial. 
samba is installed, printer is shared but I still can't see my ubuntu machine from windowsxp. 
[/COLOR]

Just now, I opened my gadmin-samba app and saw "inactive servers: For some reason windindd was uninstalled,. I reinstalled it from Synaptic. now my gadmin-samba shows no inactive server. But still I can't see my ubuntu from windowsxp

11/12/08.. This feels like a journal now; :-)
Today I realized that my web server on the same ubuntu machine is down. I couldn't browse the site couldn't even remote connect to it!. I kind of felt like checking the firewall. It seems like firewall disabled all incoming requests. I was able to enable the firewall to accept port 80 from my web site. now web server is working but my windows xp still don't see / connect to my ubuntu. It seems like something else stopping ubuntu broadcast itself to the network. If you have any suggestions please let me know please please.

11/12/08 9.26pm Things are going good. I got pissed off and uninstall all samba comoponents. then I reinstalled and configured it with this url [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) 

At least I can see the ubuntu machine now.
I configured samba with username. Is there any chance I can let users use my printer without entering username and password?
please respond. 
Thanks

---

