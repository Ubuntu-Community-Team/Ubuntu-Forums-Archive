---
title: "Motorolla v360 modem via usb"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by the_person0 on 2005-12-29
-Using a motorola phone as a modem
The following scripts placed in the indicated directories (last part is file name not directory) and with correct names will allow the pon script to connect to the Motorola v360 phone.  The phone must also be set in data/fax mode rather than the storage card this is under settings>connections after placing the scripts you use 'pon v360' to connect.  This does not damage any other part of the operating system to my knowledge so go ahead and use it but if you figure out how to fix the proceeding bug please post it.

-The problem:
whereas this works the problem that I am currently having is that when the phone disconnects the computer and phone have to be restarted before the system will work.  On the reconnect it fails on the 'MTN_GPRS-connect' specifically where it sets APN.  It would be nice if it would automatically reconnect but I am unsure how to code that.

-PPP script: [/etc/ppp/peers/v360]

/dev/ttyACM0
203400 #Speed
defaultroute #Use the network for the default root
usepeerdns #use the DNS servers from the remote network
nodetach #keep PPD in foreground
crtscts #hardware flow control
lock #lock the serial port
noauth #don't expect modem to authenticate itself
local #don'r use carrier detect or DTR
crtscts
debug


# Use the next two lines if you recieve the following messages:
# No response to echo-requests
# Serill link appears to be disconnected
# Connection terminated
#
#lcp-echo-failure 4
#lcp-echo-interval 65535

#Prevent dial line checking as it does'nt work with SE T630
#causes it to disconnect
lcp-echo-interval 0
lcp-echo-failure 0


connect "/usr/sbin/chat -v -f /etc/chatscripts/MTN_GPRS-connect"
disconnect "/usr/sbin/chat -v -f /etc/chatscripts/MTN_GPRS-disconnect"


-connect: [/etc/chatscripts/MTN_GPRS-connect]

TIMEOUT 10
ABORT 'BUSY'
ABORT 'NO ANSWER'
ABORT 'ERROR'
SAY 'Starting GPRS connection\n'

#Get the modem's attention and reset it.
"" 'ATZ'

#Selection of the PDP contect. Choose which of the data connections to use. (CID)
#'' 'AT+CGDCONT=1,"IP","",,0,0'

#Qos requirements: requested and minimum acceptable
#'' 'AT+CGQREQ=1,0,0,0,0,0'
#'' 'AT+CGQMIN=1,0,0,0,0,0'

#EO=No echo, V1=English result codes
#OK 'ATEOV1' #Can cause problems

#Set APN  [problem here]
SAY 'Setting APN\n'
OK 'AT+CGDCONT=1,"IP","internet2.voicestream.com"'

#Set APN
#SAY 'Setting APN\n'
#OK 'AT+CGDCONT=1,"IP","wap.voicestream.com"'


#Dial the number
ABORT 'NO CARRIER'
SAY 'Dialing CID 1 ... \n'
OK 'ATD*99***1#'
CONNECT ''


-disconnect: [/etc/chatscripts/MTN_GPRS-disconnect]

"" "\K"
"" "+++ATHO"
SAY "GPRS disconnected."

---

### Post by mimek on 2006-08-06
a little fix to [/etc/ppp/peers/v360]:
speed should be 230400 not 203400 or you'll get a message: *speed 203400 not supported*
I also had to add option *noipdefault* because without it I couldn't get an ip address from DHCP server.

---

### Post by DJRockoBobo on 2006-08-18
Hey hey your phone has a bluetooth port....so why don't u buy a bluetooth port which is around 25$ and u can get it working very very simple with obex bluetooth client

---

### Post by the_person0 on 2006-08-20
the usb cable charges the phone for one, second i have heard horrible things about linux and bluetooth, and third i already have a mini usb cable ;-)

---

