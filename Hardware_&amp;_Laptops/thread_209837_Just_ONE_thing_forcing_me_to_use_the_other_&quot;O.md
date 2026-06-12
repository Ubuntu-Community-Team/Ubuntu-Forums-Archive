---
title: "Just ONE thing forcing me to use the other &quot;Operating&quot; System"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by arthur on 2006-07-05
Yes! ](*,) 
I am running Ubuntu on 2 laptops and 1 desktop. The only thing keeping me from using it all the time is my UMTS-3G PCMCIA card.
I have been searching the Internet for more than a month now, I have tried all the HOW-TOs in our forum and elsewhere, to no avail (following the same procedures by the book, and more than once in all cases).
I have downloaded the installer provided by my mobile phone operator, no use.
I have even installed SUSE 10.1 and Fedora Core 5, and yet ... NOTHING.

Could anybody help? I am desperate to make it work.

My card: Novatel Merlin U630.
My operator: Telefónica (Movistar), Spain.

Any help greatly appreciated!!! :)

---

### Post by kagashe on 2006-07-06
Please post this in Hardware Help>Networking instead of Hardware Help>Laptop Support.

It seems you have posted previously on [this thread]("http://www.ubuntuforums.org/showthread.php?t=99333")
User "bvg" could make it work on Breezy so it should work on Dapper.

kagashe

---

### Post by arthur on 2006-07-06
Thanks, Kagashe!
I have tried everything I have found, and BVG has not provided details on how to make it work, that is the reason why I have opened this thread.

---

### Post by Eversmann on 2006-07-06
the evil telefonica..... ;-) sorry for posting, i couldn't hold myself ;-)

how linu treats it, a ppp device (like a modem?) or a wifi card. If it's so, maybe ndiswrapper could help on it.

But i'm speaking from the unknown. 

Novatel doesn't have a contact e-mail or phone?

---

### Post by arthur on 2006-07-06
You are right! :p 
I did contact Novatel, and they provided this solution:
[http://gprsec.hu/modules/index/](http://gprsec.hu/modules/index/)
Anyone managed to make it work with Telefónica????

---

### Post by Eversmann on 2006-07-06
Arthur, better go to ubuntu-es.org and ask there. I think we're just 4 or 5 people from spain around this forum (there's even a guy with el Fary as his avatar :-D that made me rofl)

---

### Post by arthur on 2006-07-06
Thanks, Eversmann, but I already did that.
Unfortunately, no luck.

---

### Post by xerife on 2006-07-06
[QUOTE=Eversmann]Arthur, better go to ubuntu-es.org and ask there. I think we're just 4 or 5 people from spain around this forum (there's even a guy with el Fary as his avatar :-D that made me rofl)[/QUOTE]

You´re wrong Eversman. You are not only 4 or 5 people. There´s a lot more people who are interested. In my case i´m from portugal, my brandname is kanguru from the operator optimus and crazy to find a solution for my problem which is the same as yours and amoung i there´s a lot of portuguese people in this forum and others other foruns trying to :)

---

### Post by arthur on 2006-07-06
*BTW, El Fary as an avatar is heavy stuff!!! :p :p :p *

---

### Post by patrickfromspain on 2006-07-06
I don't know what you could do, just wanted to say hello :D

Sorry it doesn't work. Really sorry you must use windows ;)

---

### Post by patrickfromspain on 2006-07-06
[QUOTE=arthur]You are right! :p 
I did contact Novatel, and they provided this solution:
[http://gprsec.hu/modules/index/](http://gprsec.hu/modules/index/)
Anyone managed to make it work with Telefónica????[/QUOTE]
have you tried it? Both telefonica and the Novatel Merlin  u630 seem to be supported.

---

### Post by arthur on 2006-07-06
Hi! :) 
I will have no other option, the problem is, I'll be forced to install a bunch of things which might produce dependency hell (some are not in our repositories ...)
Thanks for dropping by!

---

### Post by kagashe on 2006-07-07
Hi,

I am reproducing an email which is available on this page:
[http://www.orthodox.org.za/CommunityResources/vodaphone3g.html]("http://www.orthodox.org.za/CommunityResources/vodaphone3g.html")
> email message from Alan Barrett [email]tech@internet.org.za[/email]				
Success with Novatel Merlin U630 card, Vodacom, MTN, and NetBSD



This seems to be worth documenting.

I got a "Vodafone Mobile Connect 3G/GPRS data card", and a Vodacom
contract.  (The cheapest contract is "Weekender", and I added "MyMeg
250" to that, for a total price of around R350 per month, including a
free data card.)

There are apparently two cards marketed under the "Vodafone Mobile
Connect" name: one made by Option, and one made by Novatel.  I got the
Novatel card; there was no stock of the Option cards.

There's plenty of good news:  The card is not network locked (an MTN
SIM works fine in the "Vodafone" Novatel Merlin U630 card); the card
uses standard serial-over-PCMCIA protocols; it uses standard "at"
commands; neither the Vodacom nor MTN GPRS services require any weird
PPP settings; MTN's GPRS network uses proper IP addresses and I didn't
notice any weird filters.

There's also bad news: Vodacom's GPRS/3G network uses NAT and strange
filters.  You get an IP address in the 10.0.0.0/8 range, and UDP doesn't
seem to work.

The card Just Works when plugged into the PCMCIA slot of my
laptop running NetBSD.  It appears as a standard serial-over-pcmcia
port.  (Well, it appears twice, at pcmcia function 0 and function 1,
but just ignore the extra one and it works fine.)  Here's
the dmesg output:

  pcmcia0: CIS version PC Card Standard 6.1
  pcmcia0: CIS info: Novatel Wireless, Merlin UMTS Modem, U630,
  pcmcia0: Manufacturer code 0xa4, product 0x276
  com1 at pcmcia0 function 0: 
  com1: ns16550a, working fifo
  com2 at pcmcia0 function 1: 
  com2: ns16550a, working fifo

Getting PPP to work was difficult.  Nobody at Vodacom was willing to
tell me what commands to send the modem.  I figured it out by web
searches and experiment.  Two essential tricks that nobody will tell you
are:

    1) Wait a few seconds after connecting to the serial port
    before sending the PIN number.  
    Failure to do so results in "+CME ERROR".

    2) Wait 20 or 30 seconds after sending the PIN number before trying to
    dial.  
    Failure to do so results in the call appearing to go through,
    the PPP LCP negotiation starting up as expected, but the call being
    dropped after a few seconds, long before the PPP IPCP negotiation
    has completed.

Apart from that, NetBSD's regular pppd worked fine.  I assume that
FreeBSD, Linux, etc., will also work fine.  Here's a config file
for pppd:

    /dev/dty01 115200 modem crtscts
    noauth ipcp-accept-local ipcp-accept-remote
    connect '/usr/sbin/chat -v -f /etc/ppp/chat/gprs'

And here's a chat script (insert your own PIN number instead of 1234).
Much of the stuff in the chat script is for debugging, so there's
plenty of scope for simplification.


    #
    # Initialise and dial a Novatel Merlin GSM modem card.
    #
    ABORT "NO CARRIER"
    ABORT "NO DIALTONE"
    ABORT "ERROR"
    ABORT "NO ANSWER"
    ABORT "BUSY"
    REPORT "ERROR"
    REPORT "CONNECT"
    #
    # Try sending "at" several times until it works.  The card may take
    # several seconds to warm up.
    #
    TIMEOUT 2
    "" "at" OK-at-OK-at-OK-at-OK-at-OK-at-OK "\c"
    # clear any buffered data
    TIMEOUT 1 anyjunk-\c- "\c"
    #
    # Set PIN if necessary.
    #
    # First use  "at+cpin?" to see if a PIN is necessary.
    # Likely responses are
    #    "+CPIN: READY"        No PIN is necessary (or PIN has already
    #                been specified correctly).
    #    "+CPIN: SIM PIN"    The SIM needs a PIN before it will work.
    #    "+CPIN: SIM PUK"    The SIM needs the PUK (PIN unlock key),
    #                possibly after too many incorrect
    #                attempts to specify the PIN.
    #    "+CME ERROR"        Something wrong, e.g. error reading SIM,
    #                SIM not inserted correctly, SIM not yet
    #                ready soon after power-up.
    #
    # If it does not say "READY", try sending a PIN with "at+cpin=xxxx",
    # and verify that it worked by sending "at+cpin?" again.
    #
    TIMEOUT 5
    "" "at+cpin?" READY-at+cpin=1234- "\c" OK "\c"
    "" "at+cpin?" READY "\c" OK "\c"
    # clear any buffered data
    TIMEOUT 1 anyjunk-\c- "\c"
    #
    # Reset modem.  ("atz" fails if the card needs a PIN.)
    #
    "" "atz" TIMEOUT 5 OK "\c"
    #
    # It takes about 10 to 20 seconds after specifying the PIN
    # before the modem is really ready.  Delay for a while and send
    # some debugging commands.
    #
    # "at$nwrat?" should return a result like "$NWRAT: 0,2,3" if it's happy.
    # If the last digit is "0", then it is still searching for a GSM
    # network.
    #
    TIMEOUT 20
    "" "at$nwrat?" OK "\c"
    "" "\d\d\d\d\d\d\d\d\d\d\c"
    "" "at$nwrat?" OK "\c"
    "" "\d\d\d\d\d\d\d\d\d\d\c"
    "" "at$nwrat?" OK "\c"
    "" "\d\d\d\d\d\d\d\d\d\d\c"
    "" "at$nwrat?" OK "\c"
    #
    # More debugging.  The "at+clck" command should return "+CLCK: 0"
    # if the card is not network locked, or "+CLCK: 1" if the card is
    # is network locked.  "at$nwnpc=0" might give a list of networks
    # if the card is network locked.
    #
    "" "at+clck=\"PN\",2" OK "\c"
    "" "at$nwnpc=0" OK "\c"
    #
    # In the at+cgdcont command:
    #   * The first parameter is a profile number.  Just use 1.
    #   * The second parameter is always "IP".
    #   * The third parameter is the Network Access Point name (NAP).
    #    "internet" is very common.  Different providers may use
    #    different names.
    #
    # The at$nwrat? command is simply to display the modem status
    # for debugging.  The result is something like "$NWRAT: 0,2,6",
    # where the first two numbers describe the GSM capabilities of the
    # modem, and the third describes the state of communication with
    # the network.
    #   * First number: Network type
    #            0: auto
    #            1: GSM only
    #            2: WCDMA only
    #   * Second number: Circuit switched or packet switched
    #            0: circuit switched (CS) only
    #            1: packet switched (PS) only
    #            2: both CS and PS
    #   * Third number: State of communication with network.  Unlike
    #            the first two numbers, this changes over time.
    #            0: searching for a network
    #            1: WCDMS CS
    #            2: WCDMA PS
    #            3: WCDMA PS and CS
    #            4: GSM CS
    #            5: GSM PS
    #            6: GSM CS and PS
    #            (Note that 3G/UMTS seems to be classified as
    #            "WCDMA PS", while GPRS is classified as "GSM PS".)
    #
    # If the result from "at$nwrat?" ends with "0" then the modem is not
    # connected to the GSM network.
    #
    # In the atdt command, "*99***1#" is the phone number.  The "1" at the
    # end might have to match the "1" used as the first parameter to
    # the at+cgdcont command.  (Some web sites suggest using just "*99#".)
    #
    "" "at"
    OK "at+cgdcont=1,\"IP\",\"internet\""
    OK "at$nwrat?"
    OK "atdt*99***1#"
    CONNECT 


This is long email. Please read it carefully. It is giving one config file for pppd but it is applicable for NetBSD. NetBSD is detecting the device as "/dev/dty01". You must find out how Ubuntu detects it by looking at /var/log/messages file. I suggest you plug the device after booting into Ubuntu and look at the end of the file. You may get ttyUSB0 (this is how Ubuntu detects HUAWEI card) or something similar to it. The mail is giving a pppd chat script but you may not need it. After getting the device click on System/Administration/Networking/Modem connection and try to configure ppp0. On Modem Port tab just type the device identification (e.g. ttyUSB0). I hope you have the Phone no, UserID, Password etc. Just activate the "Modem connection" and see whether it works. If it does not than you need to use the chat script in the mail.

Kagashe


kagashe

---

### Post by arthur on 2006-07-07
Kagashe, thanks again!
My card is detected as a modem in /dev/ttyS0.
I already followed very similar instructions here:
[http://mybroadband.co.za/vb/showthread.php?t=21726](http://mybroadband.co.za/vb/showthread.php?t=21726)
but didn't manage to connect, although I feel I got really close.

GPRS EASYCONNECT
I did manage to download all required files to solve dependencies. Successfully installed, but unable to connect (modem is on at /dev/ttyS0, but an error message is shown every time a connection is attempted).

Never mind, I will continue using Ubuntu except when I am away from the office/home :-?

---

### Post by xerife on 2006-07-07
> **kagashe said:**
> Hi,

I am reproducing an email which is available on this page:
[http://www.orthodox.org.za/CommunityResources/vodaphone3g.html]("http://www.orthodox.org.za/CommunityResources/vodaphone3g.html")

This is long email. Please read it carefully. It is giving one config file for pppd but it is applicable for NetBSD. NetBSD is detecting the device as "/dev/dty01". You must find out how Ubuntu detects it by looking at /var/log/messages file. I suggest you plug the device after booting into Ubuntu and look at the end of the file. You may get ttyUSB0 (this is how Ubuntu detects HUAWEI card) or something similar to it. The mail is giving a pppd chat script but you may not need it. After getting the device click on System/Administration/Networking/Modem connection and try to configure ppp0. On Modem Port tab just type the device identification (e.g. ttyUSB0). I hope you have the Phone no, UserID, Password etc. Just activate the "Modem connection" and see whether it works. If it does not than you need to use the chat script in the mail.

Kagashe


kagashe

thanks a lot Kagashe.
As soon as i can, i´ll try and then i´ll post
Thanks

---

### Post by arthur on 2006-07-13
Nothing! :mad: 
Unbelievable. The worst thing: the non-existing support for Linux at Telefonica (why do they offer a Linux installer and a Linux application to connect?????)

---

