---
title: "my laptop does not like wireless cards"
date: 2010-02-24
forum: Hardware
---

### Post by hoptimusPrime on 2010-02-24
hello

a few weeks ago i picked up a used MSI 1013-L notebook.  it came with ubuntu 9.0 installed on it, and the internal wireless card worked fine.
i tried upgrading from jaunty to karmic and ran into some problems with the install, so i just reformatted and reinstalled everything.  
with a fresh install of 9.10 i no longer have wireless internet and cant seem to figure out the drivers.

the card is a RealTek RT2500pci.  there are even linux drivers for it, ive just tried so many things already i may have screwed it all up.  and im totally fine with doing a fresh install all over again if that would simplify things

i know this card should be pretty easy to use with ubuntu and there is plenty of help on the forums, i just cant seem to get it to work.  i've tried a few different things and i just need to be pointed in the right direction, im freakin pulling out my hair over this.

i also have another wireless usb adapter, equally difficult for me to install..  its the WL-6200c model, and i know, there is a few forums about that one too..  i tried ndiswrapper it just wont work!  

as you can tell, i'm new to ubuntu and i dont have any beans, but any help would be wonderful.  

maybe if i use an older or newer kernel, or maybe try a different ubuntu?  i currently have 2.6.31.  

between the two wireless cards i have, i should be able to get at least one working, right?  which ever one would be the easiest..  im plugged into a 4' ethernet cable and i feel like a dog on a leash haha

thanks for reading this, i know this a long post!
and ps i am LOVING Ubuntu!!!

---

### Post by mörgæs on 2010-02-25
If you reinstall 9.04 (supported through most of 2010) with wire and apply all updates, does the wireless card then work?

---

### Post by hoptimusPrime on 2010-02-25
thanks for the reply!
i will try that when i have some time, i'm installing on what is most likely the first "netbook" ever made, which means no dvd drive, so i'm using the live usb... i formatted the drive and now it doesn't show up.  but that is an entirely different unrelated problem which im gonna have to figure out on my own....

aanyways...  just wondering, should i install 9.04 with both of my network adapters plugged in, or should i just focus on one thing at a time.  i would really like to get this usb wireless n adapter to work as well.

but i will be happy with anything for now, all i want is wireless

---

### Post by mörgæs on 2010-02-25
You don't have to worry about formatting, it will be done automatically when you install Ubuntu. 

'Both adapters' - one with and one without cable? In the beginning just focus on getting on the web to download all updates.

---

### Post by hoptimusPrime on 2010-02-26
i'd have an answer for you by now but for some reason my bios won't recognize my usb flash drive as a boot device...  
i've tried creating sartup disks using unetbootin on a windows machine, and usb startup disk creator on ubuntu.  still, the only boot devices recognized are the hard drive and some realtek network device, not the usb drive...
i can not boot from usb to install 9.04, it does not give me that option.
im fairly sure it's not the bios, i've booted from usb before..
i'm really stuck here and this is turning out to be quite the process

oh, and by the two adapters, i meant i have an internal wireless pci card rt2500 that was working on ubuntu when i bought the machine.  and i also have a usb wireless card i just picked up, its a retail plus wl-6200c
my ideal situation would be to have both of these drivers installed and working one day

---

### Post by hoptimusPrime on 2010-02-26
as of now i am running 9.10, and everything works great except for wireless..

if i type lsusb i get:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8192 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0dd8:1400 Netac Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

the Netac on Bus 001 Device 002 is my usb flash drive i am trying to boot install jaunty from.  not seen by bios..

the Realtek semiconcuctor is the WL-6200c wireless usb adapter (i think)

if i type iwconfig, i get:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wlan5     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


i may be getting ahead of myself here, but i'm just trying to find the easiest possible way to get wireless internet on my laptop from where i am now

so it's either (1)overcome the bois usb problem somehow, do a wired install of jaunty and keep my fingers crossed for the driver to instal or (2)get either one, or possibly two of my wireless cards working in karmic as it sits now..

i really feel like throwing this laptop in a effen snow bank outside.
sorry if this makse no sense..
thanks again

---

### Post by mörgæs on 2010-02-26
After installing 9.10, did you connect by cable to download updates? There are probably hundreds of them.

Does it have a CD drive? If so you could also try booting 9.04 from a disk. Works every time, unlike a USB boot.
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

Another option is trying 10.04 Alpha. Don't panic by the word alpha, it is actually pretty stable.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by hoptimusPrime on 2010-02-26
i have installed all the updates possible for 9.10.  as of now, the enable wireless button is disabled and grey, i can not select it.  i am just using a wired connection for now.

there is no cd drive on this computer, otherwise i wouldnt bother installing with the usb. 
 my usb flas drive is still not detected as a bootable device..  

i would love to try out lucid, except i do not have any way to boot it..  

it seems like i have way too many problems to overcome just to get this wireless working

---

### Post by mörgæs on 2010-02-26
A lot of trouble at the same time... 

You could try post 5 in this thread:
[http://ubuntuforums.org/showthread.php?p=8599246](http://ubuntuforums.org/showthread.php?p=8599246)

Backports are selected changes done in 10.04 that are made available for 9.10. You could call it a 10.04 Light. 

If that does not help you could open a new thread in Absolute Beginners Talk about booting from USB. I don't have any experience in that field, sorry.

---

### Post by hoptimusPrime on 2010-02-27
i tried enabling backports using the method mentioned in your link.  unfortunately it did not work.  

i started a new thread in the networking section, the link is here:

       [http://swiss.ubuntuforums.org/showthread.php?t=1417249](http://swiss.ubuntuforums.org/showthread.php?t=1417249)

i think i will try a bit harder to get wireless working in 9.10 before i go and reinstall my os. perhaps i should take your advice and head down to beginners talk, haha

thank you for your help [mörgæs]("http://ubuntuforums.org/member.php?u=939075"), hopefully i can get this small pile of problems figured out.

---

### Post by mörgæs on 2010-02-28
You are welcome. 

It was not an insult, there is just a lot more activity in Abslute Beginners Talk.

---

### Post by hoptimusPrime on 2010-02-28
i did not take that as an insult at all
and i am very grateful for your suggestions
i'm going to open a thread in absolute beginners talk right now

---

