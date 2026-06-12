---
title: "Freecom network hard drive"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by Ianman on 2006-10-29
Hi everyone,

I was just wondering if there was some way to mount a network drive under Ubuntu. I have a Freecom network drive ([link]("http://www.freecom.com/ecproduct_detail.asp?ID=1928&CatID=8020&sCatID=1146195&ssCatID=1146196")) and under Windows I have to use software from Freecom to connect to it. Is there some way I can do this in Linux? Do I have to run the software in Ubuntu with Crossover or Wine perhaps?

Thanks for any suggestions.

---

### Post by puccaso on 2007-09-23
the network harddrive doesnt need anything extra
i think i have the model up from yours

connect your laptop to harddrive via the cable
it should give ur pc an ip automatically

goto its web interface
set the IP to something on your network.. so if ur ip on ur system via ur router/modem is 192.168.1.55 then make it something like 192.168.1.220.. 

then save it.. 
connect to ur router via eth now, and you should be able to access it anywhere on your network via [http://192.168.1.220](http://192.168.1.220) - or whatever ip you set it too.

now you'd done this - the web interface should let you create a SAMBA or FTP access/user passwords.. 

once you'v done that
you goto PLACES on the gnome/ubuntu menu and click on
CONNECT TO SERVER..

choose service type either FTP with logon or windows share

the server is 192.168.1.220 (or whatever ur harddrive is set too)

and you are up and running..

no need for extra dibble dabble like in windows

hope it helps

gimmi a shout if it doesnt

if theres linux, theres a way :)

---

### Post by jcr1 on 2008-04-04
i am really stuck on this.

I have had it working when plugged directly into the laptop, via eth. i go in and set ip address to a fixed one. 

Then what I want to do is plug it into my wireless router so i can access it over wireless network.

But as soon as i do that, i cannot access the web interface via the new (or old) ip addy. just get "unable to connect" all the time. 

Getting very frustrated now as i just cant get it to work. Done factory resets galore.

Maybe more detail...

plugged in to laptop via eth.

dhclient eth0

(somewhere around here did something like ifconfig eth0 <ipaddy>

with the OFFER addy, i went to the web interface page login: admin | admin. that gets me into the web interface.

set ip config to a fixed number.

unplug and plug into router....can no longer access web interface, let along go Places > Server

HELP!!!

Cheers,

Jon

---

### Post by jcr1 on 2008-04-04
ok update:

I can access the web interface via wireless net now!

But!!!!

I cannot access the drive as a place to save stuff.

When I go to Status in the web interface it seems to be showing up as 

Disk ID  	 IDE[0] Master, Model=[SAMSUNG SP2504C]
Free Size 	
Total Size 	none 

I get the feeling its not formatted or something? Any ideas what to do?

Cheers

---

