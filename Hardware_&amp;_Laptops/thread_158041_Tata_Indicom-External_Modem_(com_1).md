---
title: "Tata Indicom-External Modem (com 1)"
date: 2006-04-10
forum: Hardware &amp; Laptops
---

### Post by kitts on 2006-04-10
hi everyone,
             i am novice to Linux distributions. i tried slax livecd and moved onto UBuntu 5.10 (Breezy)Live cd few days on learning it has got better hardware support. Hope u people encourage me in adapting myself to Linux.
           **Tata Indicom Walky:** is a Dial up external modem (11500bps)connecting to my Compaq system on Com 1. i did read wiki on how to script tys0 etc..
          **These are already existing ways of connecting to Tata Indicom dial on Linux  (Google search):**
```
Connect your GNU/Linux box to the internet. 
U 
Connecting Ubuntu to Linux using an LSP 340E phone(FWP) for TATA Indicom / Reliance

I have myself found out the solution
create a wvdial.conf file in /etc using nano or vi or emacs with sudo( sudo nano wvdial.conf ).
then copy the following to the file



[Dialer Defaults] 

Modem = /dev/ttyS0 

Baud = 115200 

SetVolume=0 

Init1 = ATZ 

Init2 = AT+CRM=1
 
ISDN = 0 

Modem Type = Analog Modem 

FlowControl=Hardware(CRTSCTS) 

Phone = #777    

Username = <phone no>(for Rel)/ internet (for TATA)

Password = <phone no> (for Rel)/ internet (for TATA)

Stupid Mode=1 



Then create /etc/resolv.conf using vi or nano with sudo 
type:



nameserver 202.138.103.100 

nameserver 202.138.96.2



THIS SPECIFIES THE PRIMARY AND SECONDARY DNS SERVERS.
Then in terminal type 

'sudo wvdial'


and bingo u r on.
Note:
Use the sudo wvdial command repeatedly if it does not connect the first time . It sends init2 as atq0 sometimes. But works fine the next time.//Can anybody resolve this problem
I got to the net and the first thing i did was send u all the email(on the mailing list)and post it on the wiki hoping that another should not be stuck with a dialup on an otherwise fabulous ubuntu.

Those on Fedora Core and a few other distros try [http://www.geocities.yahoo.com/avinashbrathod/linux ]
```
```
[ Dialer Defaults]
Modem = /dev/ttyS0
Baud = 115200
SetVolume=0
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+CRM=1
FlowControl = Hardware (CRTSCTS)
ISDN = 0
Phone = #777
Username = internet
Password = internet
Stupid Mode = 1

----------------------------------------------
The above one is for TATA Indicom (LG-350) phone..
It works fine .....well sometimes!!,I dont know what is the
problem!,but I do some !! tricks and it works when I do the same thing
again ,it may not!,Anyways it works
U have to set the Baud rate and make next call Modem

and #wvdial Defaults

If it doesnt work,try switching off the batt and use the AC  and
sometimes when issuing the comand press the spkr phone
And the Reliance ,I think they have a Linux dialer
search google.co.in/linux..
```

 Some other links on Tata Indicom for Linux:
[http://www.linuxsolved.com/forums/ftopic1853.html](http://www.linuxsolved.com/forums/ftopic1853.html)

                Now i can figure out some scripting etc..is necessary for installation of this dial up modem. Many of the above seem to provide some solution..but i don't know how it can be worked on **Ubuntu Live Cd**
Can linux experts here suggest how i can run or make the codes work on **Terminal** of Ubunutu..and some of it has to do with Wvdial.conf:confused: 
            Can any one guide me here:-k :-| 
My Hardware details generated on running Scanmodem are attached here...

---

### Post by kitts on 2006-04-11
Can somebody help me here.:???:

---

### Post by kitts on 2006-04-15
ok no one knows anything on external modem. But i figured that i can make the above wvdial.conf and resolve.conf from the terminal using the commands
"sudo nano wvdial.conf"
but the problem i need to place the generated file into etc folder of the ramdrive which is administrative function and needs administrative login by using root.
   plz help me to login as administrator? is there a way to do it without terminal bcoz terminal makes still more difficult.

---

### Post by mips on 2006-04-15
You dont have to log in as root. Just use sudo.

Just add sudo in from of the copy command to execute the command with the equivalent of root privilages.

ie,  sudo cp filename destination-folder/filename

---

### Post by kitts on 2006-04-16
**thanks for the copy command**
                  i am connected successfully from my tata indicom from 'ubunutu Livecd'.
Now that i got everything straight ..want to make it easy for future users of UBuntu LInux connecting on Tata Indicom

1. Once you are running on Live cd open the applications>texteditor and copy the script u see on the here 
```
[Dialer Defaults] 

Modem = /dev/ttyS0 

Baud = 115200 

SetVolume=0 

Init1 = ATZ 

Init2 = AT+CRM=1
 
ISDN = 0 

Modem Type = Analog Modem 

FlowControl=Hardware(CRTSCTS) 

Phone = #777    

Username = internet

Password = internet

Stupid Mode=1 


```
2.Save the file as 'wvdial.conf' to your Desktop.
3.make another file in the text editor and copy to it the following script
```
nameserver 202.138.103.100 

nameserver 202.138.96.2
```
4.Save it as 'resolv.conf' on your Desktop
5.Open the terminal and type the following 
```
 ubuntu@ubuntu:~$ cd ~/Desktop
          and then this....
ubuntu@ubuntu:~/Desktop$ sudo cp wvdial.conf /etc/wvdial.conf 
and then.........
ubuntu@ubuntu:~/Desktop$ sudo cp resolv.conf /etc/resolv.conf
finally .........
ubuntu@ubuntu:~/Desktop$ sudo wvdial

```
bingo and you are connected..but don't forget to switch on your speaker of LG phone before you type the last command 'sudo wvdial' (otherwise the modem is notdetected).

**Note**The above script is assuming your connected to tataindicom from com1 port(ttySO). If it happens to be com 2 port then change 'ttySO' wherever u see into 'ttyS1'. :D :p :)

---

### Post by mips on 2006-04-16
So what's stopping you from installing ubuntu now or are you waiting for Dapper ?

---

### Post by kitts on 2006-04-16
[QUOTE=mips]So what's stopping you from installing ubuntu now or are you waiting for Dapper ?[/QUOTE]
i need some more time to get used to it and find all the applications i need.
But it fulfilled the most important thing...connecting my modem.

---

### Post by nandanator on 2006-09-18
Dear Linux users,



My name is Nandagopal :D (frnds call me Nandu).Im a newbie (IMEAN NEWBIE).I just started the Linux journey hardly 2

 months back.Then i realized that my Linux is incomplete without a net connection.Talking about my rig,it is an AMD64 3000+ ,512 MB DDR400 (sob sob :(  ) with nVIDIA GeForce 6100 and nForce 410.I installed Ubuntu 6.06 LTS (64 bit version) which i got it through the ShipIt scheme of Ubuntu.I started searching to find a way to connect my phone hmmmm

speaking about the connection... I am a TATA Indicom customer who is using the plan according to which  Net surfing is free between 10:00 PM and 6:00 AM.The FWP model is LG LSP 350T,with a USB interface.

My mobo is an ASUS A8N-VM and it has no Serial Port.So i had to switch to this particular model on Feb 06.

So i started Googlin ;)  the net for the right answers.I got a ton of information,but none were specific to the phone 

model which i have.I got the scrpit from net(thanx to Avinash Rathod).Also I followed a LUG from where i got the way to create a nod.

The follwoing is the way i created a nod.



mknod /dev/usb/ttyACM0 c 166 0



After this step a nod called ttyACM0 is available in my /dev.Now the next step was to identify where my USB phone modem is connected to .

So i connected it,booted the system(i use a dual boot system - > Ubuntu 6.06 and Win XP SP2),looked into the Device Manager and i found that the linux path is

/dev/bus/usb/001/002 is to which my phone is connected.So next step was to link it wwith ttyACM0..It is as follows.



ln -s /dev/usb/ttyACM0  /dev/ttyACM0



Now the next thing i did was to edit the wvdial.conf.My copy of wvdial.conf is as follows.

[Modem0]
Modem=/dev/ttyACM0
Baud=115200
SetVolume=0
Dial Command = ATDT
init1=ATZ
init2=AT+CRM=1
FlowControl= Hardware (CRTSCTS)
[Dialer tata]
Username= internet
Password= internet
Phone=#777
Stupid Mode= 1
Inherits = Modem0

Now to configure the ppp0.In the port section make an entry /dev/ttyACM0 instead of the given ttyS 's and /dev/modem.Now enter #777 in the phone number side.But i feel wvdial.conf take care of that.(since it is having built-in intelligence).

Now in the terminal type    wvdial  tata and there you have it........Happy browsing.

---

### Post by psvyas on 2007-04-10
[QUOTE=nandanator;1514681]Dear Linux users,




So i connected it,booted the system(i use a dual boot system - > Ubuntu 6.06 and Win XP SP2),looked into the Device Manager and i found that the linux path is

/dev/bus/usb/001/002 is to which my phone is connected.So next step was to link it wwith ttyACM0..It is as follows.



ln -s /dev/usb/ttyACM0  /dev/ttyACM0



Hi Nandu ,

The link command is symbolic link between /dev/usb/ttyACM0 and /dev/ttyACM0 .How do you link /dev/bus/usb/001/002 using this command?

I tried the way you said and I am able to connect for few seconds and then it gets disconnected.I think you have missed something to tell ...Please help.

Thanks.

---

### Post by psvyas on 2007-04-12
Hey I got right to surf internet with my ubuntu 6.0.6. I am connecting with USB to my tata walky. 
The simple thing is use ttyACMx if you use USB where x is the the port number.
Use ttySx if you use serial port where x is port number.

It is amazing to see that ubuntu does not need any driver sort of thing like windows...Just wvdial and thats it.
THe speed is also quit good....around 16 KB/s for download....great!!

---

### Post by questy_bin on 2007-08-22
Hi there,

I was able to dial-up to use internet using an LG-350T USB based modem. I used /dev/ttyACM0.
But the computer freezes around 10 seconds after I successfully connect. I can see that the phone shows that the net connection is still on.

Any way to debug/fix this situation.

Thanks
Questy

---

### Post by avijit on 2007-08-27
Thanks Kitti. It worked for my LG-LSP-345 also.

> **kitts said:**
> hi everyone,
             i am novice to Linux distributions. i tried slax livecd and moved onto UBuntu 5.10 (Breezy)Live cd few days on learning it has got better hardware support. Hope u people encourage me in adapting myself to Linux.
           **Tata Indicom Walky:** is a Dial up external modem (11500bps)connecting to my Compaq system on Com 1. i did read wiki on how to script tys0 etc..
          **These are already existing ways of connecting to Tata Indicom dial on Linux  (Google search):**
```
Connect your GNU/Linux box to the internet. 
U 
Connecting Ubuntu to Linux using an LSP 340E phone(FWP) for TATA Indicom / Reliance

I have myself found out the solution
create a wvdial.conf file in /etc using nano or vi or emacs with sudo( sudo nano wvdial.conf ).
then copy the following to the file



[Dialer Defaults] 

Modem = /dev/ttyS0 

Baud = 115200 

SetVolume=0 

Init1 = ATZ 

Init2 = AT+CRM=1
 
ISDN = 0 

Modem Type = Analog Modem 

FlowControl=Hardware(CRTSCTS) 

Phone = #777    

Username = <phone no>(for Rel)/ internet (for TATA)

Password = <phone no> (for Rel)/ internet (for TATA)

Stupid Mode=1 



Then create /etc/resolv.conf using vi or nano with sudo 
type:



nameserver 202.138.103.100 

nameserver 202.138.96.2



THIS SPECIFIES THE PRIMARY AND SECONDARY DNS SERVERS.
Then in terminal type 

'sudo wvdial'


and bingo u r on.
Note:
Use the sudo wvdial command repeatedly if it does not connect the first time . It sends init2 as atq0 sometimes. But works fine the next time.//Can anybody resolve this problem
I got to the net and the first thing i did was send u all the email(on the mailing list)and post it on the wiki hoping that another should not be stuck with a dialup on an otherwise fabulous ubuntu.

Those on Fedora Core and a few other distros try [http://www.geocities.yahoo.com/avinashbrathod/linux ]
```
```
[ Dialer Defaults]
Modem = /dev/ttyS0
Baud = 115200
SetVolume=0
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+CRM=1
FlowControl = Hardware (CRTSCTS)
ISDN = 0
Phone = #777
Username = internet
Password = internet
Stupid Mode = 1

----------------------------------------------
The above one is for TATA Indicom (LG-350) phone..
It works fine .....well sometimes!!,I dont know what is the
problem!,but I do some !! tricks and it works when I do the same thing
again ,it may not!,Anyways it works
U have to set the Baud rate and make next call Modem

and #wvdial Defaults

If it doesnt work,try switching off the batt and use the AC  and
sometimes when issuing the comand press the spkr phone
And the Reliance ,I think they have a Linux dialer
search google.co.in/linux..
```

 Some other links on Tata Indicom for Linux:
[http://www.linuxsolved.com/forums/ftopic1853.html](http://www.linuxsolved.com/forums/ftopic1853.html)

                Now i can figure out some scripting etc..is necessary for installation of this dial up modem. Many of the above seem to provide some solution..but i don't know how it can be worked on **Ubuntu Live Cd**
Can linux experts here suggest how i can run or make the codes work on **Terminal** of Ubunutu..and some of it has to do with Wvdial.conf:confused: 
            Can any one guide me here:-k :-| 
My Hardware details generated on running Scanmodem are attached here...

---

