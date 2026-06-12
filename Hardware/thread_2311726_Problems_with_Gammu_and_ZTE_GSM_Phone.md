---
title: "Problems with Gammu and ZTE GSM Phone"
date: 2016-01-29
forum: Hardware
---

### Post by Clockmender on 2016-01-29
Hello, it's me again...

This time I am having trouble getting a GSM phone to send out texts. I have successfully installed SMSTOOLS, GAMMU and PLAYSMS, but I keep getting the same error message when I try to send a SMS text, herewith extracts from my log file:

```

root@server1:/etc# tail -f /var/log/gammu/smsd.log
Fri 2016/01/29 17:22:53 gammu-smsd[7151]: checks: CheckSecurity=0, CheckBattery=1, CheckSignal=1
Fri 2016/01/29 17:22:53 gammu-smsd[7151]: mode: Send=1, Receive=1
Fri 2016/01/29 17:22:53 gammu-smsd[7151]: deliveryreport = sms
Fri 2016/01/29 17:22:53 gammu-smsd[7151]: phoneid = ZTE-T96-USB
Fri 2016/01/29 17:22:53 gammu-smsd[7151]: Inbox is "/var/spool/gammu/inbox/" with format "unicode"
Fri 2016/01/29 17:22:53 gammu-smsd[7151]: Outbox is "/var/spool/gammu/outbox/" with format "unicode" and transmission format "auto"
Fri 2016/01/29 17:22:53 gammu-smsd[7151]: Sent SMS moved to "/var/spool/gammu/sent/"
Fri 2016/01/29 17:22:53 gammu-smsd[7151]: SMS with errors moved to "/var/spool/gammu/error/"
Fri 2016/01/29 17:22:53 gammu-smsd[7152]: Created POSIX RW shared memory at 0x7f30651fc000
Fri 2016/01/29 17:22:53 gammu-smsd[7152]: Starting phone communication...
Fri 2016/01/29 17:23:29 gammu-smsd[7152]: Found 1 sms to "0782xxxxxxxx" with text "Hi u there, good morning!! @admin" cod 3 lgt 33 udh: t 1 l 0 dlr: 1 fls: -1
Fri 2016/01/29 17:23:29 gammu-smsd[7152]: New message to send: OUTA20160129_172321_00_07827862393_45100011100010.txtd
Fri 2016/01/29 17:23:29 gammu-smsd[7152]: Error getting SMSC from phone
Fri 2016/01/29 17:23:30 gammu-smsd[7152]: Found 1 sms to "0782xxxxxxxx" with text "Hi u there, good morning!! @admin" cod 3 lgt 33 udh: t 1 l 0 dlr: 1 fls: -1
Fri 2016/01/29 17:23:30 gammu-smsd[7152]: Same message as previous one: OUTA20160129_172321_00_07827862393_45100011100010.txtd
Fri 2016/01/29 17:23:30 gammu-smsd[7152]: Error sending SMS: No SMSC number given. Provide it manually or use the one configured in phone. (EMPTYSMSC[31])

```

and herewith my /etc/gammu-smsdrc file:

```

[gammu]
port = /dev/ttyUSB0
connection = at9600
logfile = /var/log/gammu/gammu.log
logformat = textall

[smsd]
SMSC = +447785016005
Service = files
InboxPath = /var/spool/gammu/inbox/
OutboxPath = /var/spool/gammu/outbox/
SentSMSPath = /var/spool/gammu/sent/
ErrorSMSPath = /var/spool/gammu/error/
InboxFormat = unicode
OutboxFormat = unicode
TransmitFormat = auto
DebugLevel = 1
LogFile = /var/log/gammu/smsd.log
DeliveryReport = sms
DeliveryReportDelay = 7200
CheckSecurity = 0
PhoneID = ZTE-T96-USB
PIN = ignore

```

and my smsd.conf

```

# Example smsd.conf. Read the manual for a description

devices = GSM1
logfile = /var/log/smsd.log
loglevel = 4
logfile = /var/log/sms/smstools.log
outgoing = /var/spool/sms/outgoing
checked = /var/spool/sms/checked
failed = /var/spool/sms/failed
incoming = /var/spool/sms/incoming
sent = /var/spool/sms/sent
delaytime = 6
errorsleeptime = 12
blocktime = 180
autosplit = 3
receive_before_send = yes

[GSM1]
device = /dev/ttyUSB0
incoming = yes
mode = new
#pin = 1111
smsc = 447785016005
sending_disabled = no
baudrate = 9600
report = yes
memory_start = 1
pre_init = yes
primary_memory = SM
secondary_memory = SM
secondary_memory_max = 40
needs_wakeup_at = yes

```

As you can see gammu is quite happy to read the phone's name from the config file but is not at all happy to use the SMSC number I have specified there. I have also set this number in PlaySMS (Under Gateway and SMSC settings) NOTHING works :confused: at all for me in that whatever I do I always get the same message, Does anyone have any clues as to what I should try next?

Cheers, Clock.

PS If you need more info, just ask and I will provide it, I thought it best not to bombard you with all sorts of dumps!

Oh yes, the OS is Ubuntu Sever 14.04....

---

### Post by Clockmender on 2016-02-02
Hmm - another question nobody knows the answer to...

Oh well, back to Internet searching.

Cheers, Clock.

---

### Post by howefield on 2016-02-02
To be fair, you have what is a fairly specialised sounding question which apart from you and I has been read by only one other forum member. A daily bump might attract the attention of someone who can help.

Fwiw, you might have better luck in the Server Platforms forum. Would you like the thread moved ?

---

### Post by westie457 on 2016-02-02
Hi there is a slight difference in the 'smsc=' lines.

```

[GSM1]
device = /dev/ttyUSB0
incoming = yes
mode = new
#pin = 1111
smsc = 447785016005
```

and 'gamma-smsdrc' there is a + sign at the start of the number.

This might be the cause of the issue.

Also is it really wise to have a private phone number in full view?

---

### Post by Clockmender on 2016-02-02
@westy457:

Yes spotted the + sign, but this is a red herring, i.e. not the problem, I have tried both options all ways round.......

The number is not private by the way it is the receiver number for Vodaphone UK SMS system and can be got by simply searching something like:

"What is Vodafone's UK SMSC number"

@howefield:

Yes, please move it if you think it will be better there.

Thanks, Clock.

I have since found that the SMSC number is not implemented in the gammu version in the 14.04 repos (1.33.0) - D'Oh! But the system should be reading it from the SIM in the phone, and it isn't, so I leave it open for a workaround, rather than use an unstable or non-approved version.

---

