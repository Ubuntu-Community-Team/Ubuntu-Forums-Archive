---
title: "irda on asus m6700n"
date: 2004-12-06
forum: Hardware &amp; Laptops
---

### Post by zeno on 2004-12-06
Hi all,
i have tried to install the software to use my infrared port but... even if i've read all the infrared how-to on internet, my mobile phone (nokia 8310) is never recognized, when the ir-port seems to work.
I think that my notebook needs nsc-ircc modules but i have some problems with the ir port. Has anyone installed irda on a notebook like my asus and ubuntu? Can u help me?
Bye,
zeno

---

### Post by zeno on 2004-12-08
Hi all,

finally i have the irda on!!!
My mistake was the wrong ttySX and some other things...
First of all these are the components that u need:
1.irda-utils
2.modprobe irda

On my asus laptop the irda device is at ttyS3 and not at ttyS1 as i tought. To make it ready u need this command:
> 
[stefano:ubuntu]stefano$ setserial /dev/ttyS3 uart none

After this command i needed to upgrade the irq and port of /dev/ttyS1 because i had a conflict between ttyS1 and ttyS3. Infact the output of dmesg was:
> 
nsc-ircc, Found chip at base=0x02e
nsc-ircc, driver loaded (Dag Brattli)
nsc_ircc_open(), can't get iobase of 0x2f8
nsc_ircc: Unknown parameter `id'

So i made:
> 
[stefano:ubuntu]stefano$sudo setserial /dev/ttyS1 uart none irq 0 port 0

Now u can do this command:
> 
[stefano:ubuntu]stefano$sudo modprobe nsc-ircc dongle_id=0x09

and the output of dmesg will be like this:
> 
NET: Registered protocol family 17
nsc-ircc, Found chip at base=0x02e
nsc-ircc, driver loaded (Dag Brattli)
IrDA: Registered device irda0
nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500

Now u can **modprobe irda**  and use the irattach command like this:
> 
[stefano:ubuntu]stefano$ sudo irattach irda0 -s

Finally... if u use the command **sudo irdadump** u get these lines:
> 
10:59:37.525560 xid:cmd 99787a2d > ffffffff S=6 s=0 (14)
10:59:37.615541 xid:cmd 99787a2d > ffffffff S=6 s=1 (14)
10:59:37.705526 xid:cmd 99787a2d > ffffffff S=6 s=2 (14)
10:59:37.795517 xid:cmd 99787a2d > ffffffff S=6 s=3 (14)
10:59:37.885500 xid:cmd 99787a2d > ffffffff S=6 s=4 (14)
10:59:37.975485 xid:cmd 99787a2d > ffffffff S=6 s=5 (14)
10:59:38.057437 xid:rsp 99787a2d < 236f0000 S=6 s=5 **Nokia 8310 hint=b125 [ PnP Modem Fax Telephony IrCOMM IrOBEX ] (27)**
10:59:38.065472 xid:cmd 99787a2d > ffffffff S=6 s=* ubuntu hint=0400 [ Computer ] (22)

As u can see my nokia 8310 is seen by the ir-port.

Now i have some problems with gnokii suite... another time i think that is a configuration problem. But the bigger problem is that after gnokii starts i can't use anymore irda. Infact irdadump doesn't give me any output and i need to restart ubuntu to have the ir-port ready to receive information about my nokia through the ir. Today i will "play" with this problem and if i'll have a solution i will post it here.
Hope u need this post...
Bye,
zeno

---

### Post by zeno on 2004-12-08
Hi all,
i'm another time here to explain how to use gnokii suite.

After the steps in the post before this one, you need to load two modules:
**ircomm** and **ircomm-tty**.
Then we go to configure the file **gnokiirc**
In the section [global] set the port as follow:
port = /dev/ttyS3

Then choose the right model of phone on the line
model = 

Choose connection=irda
and serial_baudrate = 115200

The last command that u need before start gnokii is:
[stefano:ubuntu]stefano$>sudo echo 115200 > /proc/sys/net/irda/max_baud_rate

Now u can start gnokii and u can communicate with your mobile phone.

Bye,
zeno

---

### Post by Nano on 2004-12-09
[QUOTE=zeno]Hi all,
i'm another time here to explain how to use gnokii suite.

After the steps in the post before this one, you need to load two modules:
**ircomm** and **ircomm-tty**.
Then we go to configure the file **gnokiirc**
In the section [global] set the port as follow:
port = /dev/ttyS3

Then choose the right model of phone on the line
model = 

Choose connection=irda
and serial_baudrate = 115200

The last command that u need before start gnokii is:
[stefano:ubuntu]stefano$>sudo echo 115200 > /proc/sys/net/irda/max_baud_rate

Now u can start gnokii and u can communicate with your mobile phone.

Bye,
zeno[/QUOTE]
 Thanks a lot for these tricks.
I'll try it now in my Medion Laptop to communicate with a Sony Ericsson.
I'll let you know.

Cheers!

---

### Post by budish76 on 2005-07-08
is setserial available on hoary version? because i cannot run this command on hoary 5.0.4 anyone can help?

---

### Post by zeno on 2005-08-03
[QUOTE=budish76]is setserial available on hoary version? because i cannot run this command on hoary 5.0.4 anyone can help?[/QUOTE]

Hi,

maybe you need to install "setserial":

```
[root@VeNuS ~]#apt-cache search setserial
setserial - Controls configuration of serial ports
[root@VeNuS ~]#
```

If you don't find anything enable universe and multiverse repositories.
Bye,
zeno

---

### Post by copperfish on 2005-08-16
This works great with my IBM Thinkpad R40 - I can sync my Tungsten T with Evolution using gpilot.

Are these settings persistent?

---

