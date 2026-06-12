---
title: "Problem sharing printer over our network."
date: 2008-09-28
forum: General Help
---

### Post by thegreatdestroyer on 2008-09-28
[SIZE=1]We have two computers on our network. The one the printer is hooked up to runs Windows Vista home edition. My computer which I'd like to be able to print to it from runs Ubuntu 8.04 with Gnome as the default desktop. I've installed samba, samba-common, and smbfs. I configured the printer and made sure the Vista pc was enabled to share the printer and files.[/SIZE]

[SIZE=1]I'm running into problems however when I try to print test pages with the printer configuration. The printer receives these jobs, I know this cause they show up in its job list and are the only jobs being sent while trying to get everything setup. They say spooling in the list, but never print. The printer physically tries to print them, but doesn't. I ran the printing troubleshooter and opened the cups error log both of which I've pasted into this pastebin [/SIZE][http://rafb.net/p/r113tc58.html](http://rafb.net/p/r113tc58.html)[SIZE=1] . The printing troubleshooter output is the first part and the error log is at the bottom. [/SIZE]

[SIZE=1]I'm very new to Ubuntu and Linux in general. I'm really not great with the technical stuff so I'm in need of a hand with this. If anyone can help please message me over Yahoo! messenger. I'm on right now and will be all day. My user name is sword_of_truth133 . If you use another service MSN, AOL, etc I can get one of those IDs as well. I just really need some one on one help with this. Your help will be greatly apprectiated :grin: .

Edit
-------

Got an MSN and ICQ handle. AOL won't let me for some reason. 

ICQ 392777641
MSN [email]iceman3@charter.net[/email]
[/SIZE]

---

### Post by thegreatdestroyer on 2008-10-03
I'm gonna post the steps I went through to configure the HP PSC 1110 printer. I'll also list other things I've done that were suggested to me.

<^paradox^> alrighty i installed samba, samba-common, smbfs
<^paradox^> i went to system > administration > printing clicked new printer
<^paradox^> selected windows printer via samba, browsed
<^paradox^> MSHOME > THECESSPOOL > PDF (thecesspool is me ubuntu) and WORKGROUP > RAC4006-PC > hp psc 1100 series appeared
<^paradox^> so i selected hp psc 1100 from WORKGROUP > RAC4006-PC
<^paradox^> then i verified
<^paradox^> and it said this print share is accessible
<^paradox^> ok so i went forward, selected hp from the database
<^paradox^> forward again and selected psc 1100
<^paradox^> i left the printer name alone then i applied 
<^paradox^> when i tried to print a test page i could see on the vista home pc jobs were appearing in its list and the printer tried to start printing them
<^paradox^> but would stop before it collected a sheet of paper
<^paradox^> in cups theyd show up in the jobs section as "completed" ;-)

As suggested I installed hplip-2.8.9. When I used hp-setup all attempts at detecting the printer failed.

I brought down the Windows firewall, still no change.

After running hp-check it returned an error saying I needed SIP so I looked it
up in Synaptic and installed sip4. Ran hp-check again still did not find SIP.

---

