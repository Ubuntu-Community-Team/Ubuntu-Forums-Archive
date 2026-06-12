---
title: "Connecting to the internet via a1200 bluetooth"
date: 2006-12-09
forum: Hardware &amp; Laptops
---

### Post by lingnoi on 2006-12-09
Before trying to use my Motorola A1200 as a bluetooth modem I had been quite happliy using my older Motorola v365 with the same phone company. 

The problem seems to be more with connecting to the internet via the phone propperly then anything else but I just don't know what I should do to get it working.

/chatscripts/BluetoothDialup
```
TIMEOUT 35
ECHO    ON
ABORT   '\nBUSY\r'
ABORT   '\nERROR\r'
ABORT   '\nNO ANSWER\r'
ABORT   '\nNO CARRIER\r'
ABORT   '\nNO DIALTONE\r'
ABORT   '\nRINGING\r\n\r\nRINGING\r'
''      \rAT
OK      ATD*99***1#
CONNECT ""
```

Here is a log of what I get once I type "pon BluetoothDialup"
```
Dec  5 13:08:53 localhost pppd[7604]: pppd 2.4.4 started by andrew, uid 1000
Dec  5 13:08:56 localhost chat[7609]: timeout set to 35 seconds
Dec  5 13:08:56 localhost chat[7609]: abort on (\nBUSY\r)
Dec  5 13:08:56 localhost chat[7609]: abort on (\nERROR\r)
Dec  5 13:08:56 localhost chat[7609]: abort on (\nNO ANSWER\r)
Dec  5 13:08:56 localhost chat[7609]: abort on (\nNO CARRIER\r)
Dec  5 13:08:56 localhost chat[7609]: abort on (\nNO DIALTONE\r)
Dec  5 13:08:56 localhost chat[7609]: abort on (\nRINGING\r\n\r\nRINGING\r)
Dec  5 13:08:56 localhost chat[7609]: send (^MAT^M)
Dec  5 13:08:56 localhost chat[7609]: expect (OK)
Dec  5 13:08:56 localhost chat[7609]: ^MAT^M^M
Dec  5 13:08:56 localhost chat[7609]: OK
Dec  5 13:08:56 localhost chat[7609]:  -- got it 
Dec  5 13:08:56 localhost chat[7609]: send (ATD*99***1#^M)
Dec  5 13:08:57 localhost chat[7609]: expect (CONNECT)
Dec  5 13:08:57 localhost chat[7609]: ^M
Dec  5 13:08:57 localhost chat[7609]: ATD*99***1#^M^M
Dec  5 13:08:57 localhost chat[7609]: CONNECT
Dec  5 13:08:57 localhost chat[7609]:  -- got it 
Dec  5 13:08:57 localhost chat[7609]: send (^M)
Dec  5 13:08:57 localhost pppd[7604]: Serial connection established.
Dec  5 13:08:57 localhost pppd[7604]: Using interface ppp0
Dec  5 13:08:57 localhost pppd[7604]: Connect: ppp0 <--> /dev/rfcomm0
Dec  5 13:08:58 localhost pppd[7604]: Remote message: Welcome to Motorola Ezx Software Modem!
Dec  5 13:08:58 localhost pppd[7604]: PAP authentication succeeded
Dec  5 13:08:59 localhost pppd[7604]: LCP terminated by peer (^@^@^@^@^@^@)
Dec  5 13:08:59 localhost pppd[7604]: Hangup (SIGHUP)
Dec  5 13:08:59 localhost pppd[7604]: Modem hangup
Dec  5 13:08:59 localhost pppd[7604]: Connection terminated.
Dec  5 13:09:00 localhost pppd[7604]: Exit.
```

As you can see the problem exists with this "LCP terminated by peer (^@^@^@^@^@^@)"

Googling has not helped at all. Are there any smart people out there who know what I am doing wrong?

Thanks! ](*,) :D

---

### Post by lingnoi on 2006-12-29
I've been trying to find an answer to this problem for weeks now. Does anyone have any suggestions I could try. 

I am fresh out of ideas. :-k

---

### Post by mthakur2006 on 2006-12-31
yeah i am having the exact same problem but i am using three mobile network ,..

---

### Post by lingnoi on 2007-01-29
I've finally figured it out how to connect.

```
debug
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/BluetoothDialup"
usepeerdns
/dev/rfcomm0 115200
defaultroute
noipdefault # added this line
crtscts
lcp-echo-failure 0

:210.4.139.129 # Your external ip address from the phone
```

Not sure if you need the IP address (which will be different for you phone anyway) but this setup is working.

:D

---

### Post by nicksukharev on 2007-06-15
> **lingnoi said:**
> 

:210.4.139.129 # Your external ip address from the phone[/CODE]

Not sure if you need the IP address (which will be different for you phone anyway) but this setup is working.

:D

You do need an IP address with ROKR E6 as it appears. At least it works with t-zones with this setup and breaks if I comment the IP out. I wonder what is the significance of this IP.

---

