---
title: "How to use internet by cell phone through USB or bluetooth"
date: 2008-04-26
forum: Hardware
---

### Post by dropshot on 2008-04-26
Hi all,
The biggest reason I'm not using linux (of any flavor) is that i haven't managed to configure my internet connection. It's kinda annoying to do that in linux because you need a connection to do so.

So, I use my laptop, a thinkpad r61, with my sony ericsson k800i. In windows xp, i have two options: bluetooth pan (internet shared through bluetooth) or usb cable (by enabling USB internet on my phone).

Making either work would be great. But i don't have much free time or spend much time at friend's house to figure out which guides/methodes would work... in fact i haven't installed the new *buntu yet (don't know which one i'll try).

So could you recommend me some guides that have worked?

---

### Post by lsearcey on 2008-04-26
I have the same problem I havn't made the full jump because of not being able to use my Motorola razr as a modem.  I'm in the process of using virtual box to be able to connect.  Anyone else have any ideas?

---

### Post by AlanR8 on 2008-04-26
This was an issue for me as well, Nokia (currently 6300 in the UK on Vodaphone). That said, the fix was easier than I thought. All I did was:

Found the file in the etc/ folder called wvdial.conf
Backed it up
Opened it as Root so I could edit
Deleted the contents
Pasted the following into the file

Code
> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99#
Password = A
Username = B
Stupid Mode = 1

Saved the file.

All I do now is connect the Nokia by USB and then select Nokia Mode on the phone.
Open a terminal and type:

sudo wvdial

This opens the modem and bingo you're on the web.

I can't take credit for this, I picked it up somwhere on this forum but it works with Nokia and in the UK.

---

### Post by quickwitt on 2008-04-30
I can confirm a similar setup with a RAZR V3xx in Heron. Works like a champ although I do have some stalling in downloads of large files. Still looking for the fix to that issue.

---

### Post by zakaria.cse on 2008-05-03
> **AlanR8 said:**
> This was an issue for me as well, Nokia (currently 6300 in the UK on Vodaphone). That said, the fix was easier than I thought. All I did was:

Found the file in the etc/ folder called wvdial.conf
Backed it up
Opened it as Root so I could edit
Deleted the contents
Pasted the following into the file

Code


Saved the file.

All I do now is connect the Nokia by USB and then select Nokia Mode on the phone.
Open a terminal and type:

sudo wvdial

This opens the modem and bingo you're on the web.

I can't take credit for this, I picked it up somwhere on this forum but it works with Nokia and in the UK.

Excellent! It works for me instantly with my Nokia 5700 & GrameenPhone GPRS/Edge connection, Bangladesh.

---

### Post by saipu on 2008-05-03
> **dropshot said:**
> Hi all,
The biggest reason I'm not using linux (of any flavor) is that i haven't managed to configure my internet connection. It's kinda annoying to do that in linux because you need a connection to do so.

So, I use my laptop, a thinkpad r61, with my sony ericsson k800i. In windows xp, i have two options: bluetooth pan (internet shared through bluetooth) or usb cable (by enabling USB internet on my phone).

Making either work would be great. But i don't have much free time or spend much time at friend's house to figure out which guides/methodes would work... in fact i haven't installed the new *buntu yet (don't know which one i'll try).

So could you recommend me some guides that have worked?

I use Ubuntu Gutsy and K530i. Just plug in the phone to usb port, choose 'phone mode' and I've got myself an internet connection. :) (of course need to activate phone GPRS/3G setting)

---

### Post by dropshot on 2008-05-03
> **AlanR8 said:**
> This was an issue for me as well, Nokia (currently 6300 in the UK on Vodaphone). That said, the fix was easier than I thought. All I did was:

Found the file in the etc/ folder called wvdial.conf
Backed it up
Opened it as Root so I could edit
Deleted the contents
Pasted the following into the file

Code


Saved the file.

All I do now is connect the Nokia by USB and then select Nokia Mode on the phone.
Open a terminal and type:

sudo wvdial

This opens the modem and bingo you're on the web.

I can't take credit for this, I picked it up somwhere on this forum but it works with Nokia and in the UK.
That's not really what I was trying to do, it doesn't involve any modems.
> **saipu said:**
> I use Ubuntu Gutsy and K530i. Just plug in the phone to usb port, choose 'phone mode' and I've got myself an internet connection. :) (of course need to activate phone GPRS/3G setting)
I had to reset the USB Internet mode. For some reason it doesn't work directly. Works fine now.

---

### Post by wijit on 2008-08-16
Many of posted messages here and other places show how-to's on a service that are not applicable in Thailand. In other countries it seems to me that dialing *99# from your edge/gprs enabled mobile will connect you to the internet. In Thailand, the dail-out number is *9000 but it does not connect you to the internet immedietly. You are required to listen to an automatic notifier and press the key in response to the voice in order to select a certain type of services (service fees, actually). After you have got an SMS notifying you are ready to connect to the internet, on Windows, you will notice the pop-up messages the modem (your mobile) is found. You will now activate the connection software and make a connection. I want to use my Ubuntu (7.10 Gutsy) to connect to the internet. Please suggest which part of the wvdial.conf I can modify to make it work. Or, are there any other ways I can make a dial manually on the mobile then Ubuntu recognises that now there is a connection(IP) available for it. Thanks.:KS

---

### Post by wijit on 2008-09-03
First of all, I've to apologize everyone who visited this page for my own lacking of knowledge. I used Gutsy 7.10 on 3 different computers, namely, ECS green 773, Acer TravelMate 4720 and a home-made PC. After studying from several topics around this plus a reading some related man-pages, I thought I understand some fundamental idea about how the system works. Truemove, the network provider I use, provides 2 steps for prepaid mobile phone users to follow to make their mobiles to be GPRS capable. First, a user dials 9779 for Truemove sending brand and model specific information back to install in the phone. Dial out number (*99#), username and password for GPRS connection are internally set in this step. If this step succeeds the phone is GPRS capable. Next, at times the user want to utilise the service, the user dials *9000. The user is asked to select, among several types of services, a service she wants to use during the conversation. At the end of this step, Truemove will send a SMS notifying the user that the GPRS connection is ready. Thanks to the palm and mobile internet forums where Thai people have been talking about this since the availability of public (free and paid) WAP (at least 2 years ago), for information and turning the light on for me. They have to make a dial-up connection and use the specific phone number *99# which is the same as a parameter of the "phone" field in the wvdial.conf shown by many topics in Linux forums. Thanks to you all too. The two steps I explained above just make the mobile phone connected to the ISP. When we need to use our computer to connect to the internet we need to connect the computer to the GPRS connected mobile phone which now acts as as a GPRS modem. And that is the role of the wvdial command which, inturn, get preset information from the configuration file wvdial.conf. Actually, the file wvdial.conf comes with Gutsy, but I did not guarantee to be true for other distributions, and can be found in /etc. There are 4 lines (fileds) in the file context, namely, Phone, Username, Password and New PPPD. The first 3 lines have their parameters left blank. The last line has a preset parameter of "Yes" (with no quots). We can modify and use this file or create a new configuration file. However, since there are ways to stipulate the wvdial.conf to suit purposes, as suggested in the man-page, creation of new configuration file seems to be not encouraged. If we have a GPRS connected mobile phone connected to the computer on a USB port, we can easily modify the wvdial.conf by issuing the command "sudo wvdialconf /etc/wvdial.conf". The command will find and initialise the modem and send basic fields to the configuration file. However, we are required to put new information and make some modification to the file context. Normally, what we get after issuing the command is six additional fields, namely, Init1, Init2, Modem Type, Baud, Modem and ISDN, and the 3 blank fields become commented out. All added fields come with their (deemed to be good) parameters. We can use our pseudo root privileges to edit this file, for example, by issuing the command "sudo gedit /etc/wvdial.conf". What we need to add to the file is a field "Init3" and its parameter "AT+CGDCONT=1,"IP","internet"". This parameter varies depending upon the ISP you use. If you do not know you have to ask the ISP or someone who know. Since this information is ISP-specific, you cannot guess or apply by those provided by other ISP's, Also you have to uncomment to the original three blank fields and feed them with parameters. Normally, the phone's parameter is "*99#" and I've seen this is the same for several countries. For the fields Username and Password, you can either ask your ISP or take them from your ISP's suggestion when you first did made your mobile a GPRS capable (in case you can remember). Mine is "1234" for both. After saving the file you can try "sudo wvdial" and if you see IP's (local and remote) and DNSes information it means you are connected to the internet. Now, until disconnected, you can use your browser and/or your internet tools as usual. Please forgive me for weakened English and my stupid questions above.

---

### Post by XdanishXcowboyX on 2011-03-31
can someone please tell me, step by step, how to use my tmobile mytouch 3g as a modem?

i have a bluetooth dongle. both devices are bluetooth ready, i just cant figure out how to do it.

im new to ubuntu, so i have no clue what im doing.

thanks

---

