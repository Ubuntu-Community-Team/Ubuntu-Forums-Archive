---
title: "usrobitics in ubuntu hoary"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by unisol on 2005-05-17
i got my modem to dial up bt typing ln -s ttyS14 and i could dial up however it doesnt hold the connection anybody know why

---

### Post by wwwolf on 2005-05-17
[QUOTE=unisol]i got my modem to dial up bt typing ln -s ttyS14 and i could dial up however it doesnt hold the connection anybody know why[/QUOTE]

Hmmm, what interface were you using to dial in? 'pppd call isp'?, 'wvdial'? 

I assume that by creating the link above, you meant to /dev/modem?

try 'wvdialconf' and see if it sets it up for you automagically. You then just need to edit /etc/wvdial.conf to put in the phone#, username, and password. You then use 'wvdial' to connect.

or you can try, after making the link to /dev/modem, run 'sudo pppconfig ISP' and set up that way, then use 'pon ISP' to connect and use 'poff' to disconnect.

Its really hard to diagnose your problem without knowing what interface you're using or what the error code was.   [-X 

But, you are correct in that ttyS14 is the default port for this modem.  :-P 

HTH,

---

### Post by unisol on 2005-05-18
yes it is ttyS14 the instructions with the modem say to use ttySX but ttys14 is where thenmodem port is.i run pppconfig but it says it cant find the config file same with wvdial and minicom initializes the modem but you cant type AT command in the minicom box, maybe im not using the interfaces right.i tried installing gnomeppp but when i get to ./configure it tells me i dont have the right libs installed i install them but it still wont get past./configure any help would be appreciated linux makes me feel retarded i keep telling myself it cant be that hard also when i try to activate ppp0 when i go to the modem tab the port is not in there i have to manually enter i thought it should be in there

---

### Post by trash on 2005-08-26
sudo apt-get install gnome-ppp

should do ya:)

---

