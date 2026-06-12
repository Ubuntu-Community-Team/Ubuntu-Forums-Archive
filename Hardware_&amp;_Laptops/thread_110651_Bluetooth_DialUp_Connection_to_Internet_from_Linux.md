---
title: "Bluetooth DialUp Connection to Internet from Linux :-("
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by arunbabu on 2005-12-31
Its now a long time since I am asking every person I see and meet ... How to connect my bluetooth adapter (connected to my USB) communicate with my mobile Nokia 6600. I just have the software given with the hardware - Bluesoleil from IVT Corporation ... This made me switch to Windows Xp .. Could some one pull me out ?

Hardware

1. Bluetooth adapter - Billionton
2. Nokia 6600 mobile with Internet
3. My Linux Box

Can someone help me connect all three to connect INTERNET

---

### Post by arunbabu on 2005-12-31
help me please :(

---

### Post by emperon on 2005-12-31
Same here, this is the only reason i am using windows. 
I am currently reading linux unwired which dedicates  seperate chapters each for bluetooth and GPRS topics though i am dubious if it could be helpful. Please someone help us.

---

### Post by arunbabu on 2006-01-01
Why isnt any one replying ... hmmm ... it seems I'll have to go the windows way, since its the only option ... Mandriva people too are dumb !!!

---

### Post by emperon on 2006-01-02
Hello, i have just succeeded to connect gprs via bluetooth. Currently i am writing from there.

I have read wirless hacks of oreilly and 
found the solution

1-) Make sure that you have the appropriate hardware ready. (I tried same phone and notebook in windows it was working.)

2-) Makesure that bluez-utils is installed via package manager

3-)open a console and type   **hcitool scan** this should give you the  BD address of your phone, take a note of this number

4-)type ** sdptool search DUN ** from the out put take a note of channel number

5-)make sure that you have written your pin number in /etc/bluetooth/pin (any 4 digit number is ok , you will use the same number through the phone)

6-) type [B]# rfcomm bind /dev/rfcomm0 00:11:22:33:44:55:66 *channel_number_noted* [B]  using the channel number noted earlier

7-) test it by typing ** rfcomm ** , you should see the channel is clear or closed, both are ok e.g.   rfcomm0: 00:11:22:33:44:55 channel 1 clean

8-) create the following file as  root : /etc/ppp/peers/gprs

9-) Put the following inside:
```

 
/dev/rfcomm0
connect '/usr/sbin/chat -v -f /etc/ppp/peers/gprs.chat' 
        noauth 
        defaultroute 
        usepeerdns 
        lcp-echo-interval 65535 
        debug 

```

10-) Create the following file as root: /etc/ppp/peers/gprs.chat' and put the following
```

TIMEOUT                 15         
ECHO                    ON 
HANGUP                  ON       
''                              AT 
OK                              ATZ      
OK                              ATD*99*# 

```
Here you may need to change *99*#, it should be the number you dial. In Turkey it is that, in some countries it is *99# or *99***1#, consult your GSM provider.

11-) Go to your phone and initiate pairing by using the same pin and confirm all things from phone

12-) type ** sudo pppd call gprs ** and confirm the connection with your phone

That's it, your gprs connections should be working now, enjoy surfing

---

### Post by emperon on 2006-01-02
Hello, i have just succeeded to connect gprs via bluetooth. Currently i am writing from there.

I have read wirless hacks of oreilly and 
found the solution

1-) Make sure that you have the appropriate hardware ready. (I tried same phone and notebook in windows it was working.)

2-) Makesure that bluez-utils is installed via package manager

3-)open a console and type   **hcitool scan** this should give you the  BD address of your phone, take a note of this number

4-)type ** sdptool search DUN ** from the out put take a note of channel number

5-)make sure that you have written your pin number in /etc/bluetooth/pin (any 4 digit number is ok , you will use the same number through the phone)

6-) type ** rfcomm bind /dev/rfcomm0 00:11:22:33:44:55:66 *channel_number_noted* **  using the channel number noted earlier

7-) test it by typing ** rfcomm **  you should see the channel is clear or closed, both are ok e.g.   rfcomm0: 00:11:22:33:44:55 channel 1 clean

8 -) create the following file as  root : /etc/ppp/peers/gprs

9-) Put the following inside:
```

 
/dev/rfcomm0
connect '/usr/sbin/chat -v -f /etc/ppp/peers/gprs.chat' 
        noauth 
        defaultroute 
        usepeerdns 
        lcp-echo-interval 65535 
        debug 

```

10-) Create the following file as root: /etc/ppp/peers/gprs.chat' and put the following
```

TIMEOUT                 15         
ECHO                    ON 
HANGUP                  ON       
''                              AT 
OK                              ATZ      
OK                              ATD*99*# 

```
Here you may need to change *99*#, it should be the number you dial. In Turkey it is that, in some countries it is *99# or *99***1#, consult your GSM provider.

11-) Go to your phone and initiate pairing by using the same pin and confirm all things from phone

12-) type ** sudo pppd call gprs ** and confirm the connection with your phone

That's it, your gprs connections should be working now, enjoy surfing

---

### Post by arunbabu on 2006-01-13
sorry ... i took so long to thank you ... actually i forgot about the post :( and was into other ways to find a solution ...

Good work Emperon !!! and i am really thankfull to you !!!

i have found some useful links too ... may be you will like them too 
[http://www.cs.helsinki.fi/u/mraento/symbian/bt-ap.html](http://www.cs.helsinki.fi/u/mraento/symbian/bt-ap.html)
[http://www.unix-ag.uni-kl.de/~leonard/linux-n6600-howto.html](http://www.unix-ag.uni-kl.de/~leonard/linux-n6600-howto.html)
[http://www.russellbeattie.com/notebook/1001649.html](http://www.russellbeattie.com/notebook/1001649.html)

arun babu

---

### Post by arunbabu on 2006-01-13
Hey emperor it didnt work out for me !!! :( 
>12-) type  sudo pppd call gprs  and confirm ...
I got stuck there ... it shows "script failed" after a while ... everything about it works great ... 

>>>>
It's quite easy to use Linux as the Bluetooth access point instead of Windows and mrouter. Basically you have to (these are written from memory, so caveat emptor):

    * Have your Linux box configured as a router with NAT.
    * Install bluez, bluez-libs, bluez-sdp, bluez-pan, bluez-utils.
    * Get bluetooth working (test that you can see your phone with sdptool browse)
    * Run sdpd
    * Add the serial port to your services with sdptool add --channel=3 SP
    * Run dund with something like dund --listen --channel 3 --msdun noauth 169.254.1.68:169.254.1.1 crtscts 115200 ms-dns YOUR_DNS_SERVER lock
    * Get and run kannel
    * The first time using this, to get the phone to connect to your machine for Bt serial:
    * rfcomm bind 4 <phone's Bt address> <phone's BT serial port service channel>
    * echo x > /dev/rfcomm4

Use the output from sdptool browse to figure out your phone's address and the channel number for the serial port. By connecting to the phone you trigger mrouter on it, which will try to connect back and store the PC's Bluetooth address (and channel) as the preferred serial connection

6600: change the addresses above to something else than 169.254.x.x. Don't set up a login script on the phone, since this is RAS specific.

If you are using Linux you don't have to set up the username and password. It should work with them set as well, though. **Do not try to use authentication with pppd**. It's very easy to crash the phone with it. It seems the ppp stack is not very good at handling authentication options it doesn't understand :-/.

You can read a description of setting up a P800 with linux for a more in-depth description of the issues involved. Note that we are not using the mrouter stuff here, so we don't need any DNS records, and the phone initiates the connectionw without having to send stuff to it's serial port.
>>>> from [http://www.cs.helsinki.fi/u/mraento/symbian/index.html](http://www.cs.helsinki.fi/u/mraento/symbian/index.html)

lemme see to figure out what the problem is ... pls help me if u have time

---

### Post by emperon on 2006-01-17
[QUOTE=arunbabu]Hey emperor it didnt work out for me !!! :( 
>12-) type  sudo pppd call gprs  and confirm ...
I got stuck there ... it shows "script failed" after a while ... everything about it works great ... 

[/QUOTE]

try this instead of step 12:

sudo pppd nomagic call gprs

If still doesn't work, try to investigate your var/log/messages  and var/log/syslog they should identfy the problem

---

### Post by trompie on 2006-01-18
hey dude!
i have the same problem as you, and this other guy replied that u should go to the console and therefrom on...
but then it picks up the adapter but you need the bluesoleil to connect to the internet.
That is same reason i'm also using XP.
Why can't they make the application compatible with Ubuntu???
Linux is compatitble but not Ubuntu!
What is that reason?

---

### Post by emperon on 2006-01-19
I don't know. But I can CLEARLY tell you that I CAN CONNECT to Internet by only using the guide I post above and it works for me. My phone is also nokia 6230. But i admit it took a few hard days to resolve my problems.

---

### Post by Roner on 2006-05-28
See my post here
[http://www.ubuntuforums.org/showpost.php?p=1061836&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1061836&postcount=26)

For a less complex solution.

---

