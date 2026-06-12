---
title: "i installed xubuntu 10.10, netbook mouse doesnt work anymore"
date: 2010-12-29
forum: Hardware
---

### Post by dare2wow on 2010-12-29
so today i installed xubuntu on my aspire one.
everything is great the only problem is that the mouse does not work, if i click nothing happens, if i try to move the cursor nothing happens. i have been using a usb mouse all day.

this is what i get when i do xinput list

> bobo@bobo-AOA150:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627;** SynPS/2 Synaptics TouchPad**              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Chicony USB Multimedia Wireless Kit     	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Acer Crystal Eye webcam                 	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Chicony USB Multimedia Wireless Kit     	id=13	[slave  keyboard (3)]
bobo@bobo-AOA150:~$ 

so im guessing that its detected but for some reason it does not work.

---

### Post by manorchurch on 2011-01-05
Hi. I also have an Aspire One. Original installation was without any external mouse -- touchpad "as is". After initial Xubuntu installation, I added a basic wired HP USB optical mouse.  It worked just fine.  I loaned it out for a day for an acquaintance to use for a business trip.  He disdained the wired mouse, and plugged in a Logitech wireless USB optical mouse, which worked also just fine. 

However, when I plugged the wired HP USB mouse, xinput now identifies it as a "Logitech USB".  It moves the pointer, but the buttons don't work correctly.

Sorry about not including the xinput listings, but you probably know how irritating it is to cut and paste with the Aspire touchpad.

My assumption is that the device is mis-identified in plugnplay USB routine. Perhaps your issue has related origins. How extensive are affected related operations, I don't know.

---

### Post by perezomail on 2011-01-08
I n my case I upgraded from lucid for the better codec support everything worked like a champ until about a week and a half ago when my samba shared disappeared and after taking to someone on launch pad for a spell they came back again on the 5th of this month through and update involving smb shares however I was going to let the people on launchpad know that everything was fine now and suddenly my mouse went out. I did managed to let them know i had mouse troubles which is why it took me so long to reply.

me really thinks it has something to do with the updated coming down the pike
Im on an acer one which came with linux installed but reconditioned with bluetooth on an 8gig hd with 512 ram

i boot up fine and when i try to hit something like the no snooze on the upper panel or the menu or simply scroll my mouse any where my left click window comes up and there i am mouse less meerkat 10:10 gnome.
im going to try waiting this one out maybe enough complaints from people whose mouse are working in other computers will get things coming down the update pike again im just afraid of whats next
BOOM

---

