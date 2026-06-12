---
title: "DVB-T tuner advice?"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by c-m on 2005-08-20
Due to my WinTv-Go card being a complete failure under linux, I plan on purchasing a dvb-t card. This time however i want to do things right and make sure whichever card i choose is well supported, used and documented in linux.

Can anyone provided me with any recommendations?

Thank you.

[COLOR=Red]Edit: I have recently come accross this:  [email]amitsemail@ukf.net[/email]   Anyone considering using a dvb-t, dvb-s or dvb-c card please view this page, it offers a complete list of DVB devices currently supported by linux kernels or drivers. Hopefully you will aviod the headache of buying a poorly supported card.[/COLOR]

---

### Post by stepper on 2005-08-20
Can u please explain complete (WinTv-Go) failure?
Card not detected?
can u post your lspci?

---

### Post by Jussi Kukkonen on 2005-08-20
The Hauppauge 250/350 seem to be most popular (EDIT: this observation is from a small sample, though).

Here is a list of some cards that have linux drivers: [http://pvrhw.goldfish.org/tiki-page.php?pageName=pvrhw_tuners](http://pvrhw.goldfish.org/tiki-page.php?pageName=pvrhw_tuners)

---

### Post by c-m on 2005-08-20
[QUOTE=stepper]Can u please explain complete (WinTv-Go) failure?
Card not detected?
can u post your lspci?[/QUOTE]
 i do already have a thread about this card, the card is working in the sense that both Tvtime and xawtv will find a signal and display a picture. the problem is that i do not have any sound.

while the picture is fine, the only sound i get from TV is static or white noise, on every channel. The strange thing is that if i plug say my x-box or something into the composite in and line in on the WinTV-GO then i get sound from that, so i don't understant why it doesn't work with normal TV.

lspci concerning the card lists:  (i don't why its detected as winfast tv2000 xp)

> 
0000:01:07.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
0000:01:07.1 Multimedia controller: Conexant: Unknown device 8811 (rev 05)


@ [Jussi Kukkonen] the PVR 250/350 are only analog card afaik. btw a bit OT but do you get 24hrs of day light in finland at the moment, or is that further north?

---

### Post by stepper on 2005-08-20
c-m, here is a stupid suggestion:

Since I see your card was autodetected from your [previous thread](http://ubuntuforums.org/showthread.php?t=55587), may I suggest that you "sort of" load the modules yourself by following the steps in this [site](http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm) with your card number being either 34 or 80.

---

### Post by c-m on 2005-08-20
[QUOTE=stepper]c-m, here is a stupid suggestion:

Since I see your card was autodetected from your [previous thread](http://ubuntuforums.org/showthread.php?t=55587), may I suggest that you "sort of" load the modules yourself by following the steps in this [site](http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm) with your card number being either 34 or 80.[/QUOTE]
 are you refering to this:

> 
With a Debian (kernel 2.6.x), in the past, modules were loaded through the /etc/modprobe.conf file. The /etc/modprobe.conf file was remplaced by this one:  /etc/modprobe.d/old_etc_modprobe.conf
Now you can configure the bttv driver through this file: /etc/modprobe.d/bttv.
Here is an example:

# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# Askey TV Capturer
options bttv card=59 tuner=0 radio=0 pll=1 adc_crush=0 


there is no old_etc_modprobe.conf in /etc/modprobe.d, but i've gone ahead and created the bttv file anyway. Although i'm sure my card uses the cx238811 or something chipset.

the site doesn't give any instructions on what to do after creating the bttv file in /etc/modprobe.d/bttv. What does /etc/modules file do then?

---

### Post by stepper on 2005-08-21
[QUOTE=c-m]
there is no old_etc_modprobe.conf in /etc/modprobe.d, but i've gone ahead and created the bttv file anyway. Although i'm sure my card uses the cx238811 or something chipset.

the site doesn't give any instructions on what to do after creating the bttv file in /etc/modprobe.d/bttv. What does /etc/modules file do then?[/QUOTE]
To create the bttv conf file you do this:
```
sudo gedit /etc/modprobe.d/bttv
```
and then make it look like this:
> 
# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# Askey TV Capturer
options bttv card=59 tuner=0 radio=0 pll=1 adc_crush=0 
 Go back to that site and look for your appropriate tuner PAL or NTSC or whatever and be sure to change your card number. In your case I think its 34 or 80.

/etc/modules contains the modules to be loaded when your system boots. Be sure to put the bttv module in there aswell
```
sudo gedit /etc/modules
```
and then put bttv in the bootom of the list. for example
> ........
ide-core
........
bttv


---

### Post by c-m on 2005-08-21
i don't have a clue what you are talking about. i have already created the the bttvfile by using nano -w /etc/modprobe.d/bttv (a habibit from my gentoo days).

My card and tuner are set to the correct type i.e 80 for the card and 1 for the tuner (phillips pal_i)

what else is there to do after that? TvTime still only plays static as sound?

---

### Post by Hamman on 2005-08-22
[QUOTE=c-m]Due to my WinTv-Go card being a complete failure under linux, I plan on purchasing a dvb-t card. This time however i want to do things right and make sure whichever card i choose is well supported, used and documented in linux.

Can anyone provided me with any recommendations?

Thank you.

[COLOR=Red]Edit: I have recently come accross this:  [email]amitsemail@ukf.net[/email]   Anyone considering using a dvb-t, dvb-s or dvb-c card please view this page, it offers a complete list of DVB devices currently supported by linux kernels or drivers. Hopefully you will aviod the headache of buying a poorly supported card.[/COLOR][/QUOTE]
[This](http://linuxtv.org/wiki/index.php/PCI_devices_DVB-T) might be of help. The AverMedia 771/761 seems nice.

---

