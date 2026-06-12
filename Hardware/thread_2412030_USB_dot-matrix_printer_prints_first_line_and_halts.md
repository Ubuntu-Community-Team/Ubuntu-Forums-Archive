---
title: "USB dot-matrix printer prints first line and halts"
date: 2019-02-07
forum: Hardware
---

### Post by lgastmans on 2019-02-07
I revert to the community after trying my best to get the following printer to work on Ubuntu 16.04 (and Ubuntu 18.04):

[https://www.tvs-e.in/product-detail-db.aspx?id=37&typ=btn_bt&pro=tb_9#downloads](https://www.tvs-e.in/product-detail-db.aspx?id=37&typ=btn_bt&pro=tb_9#downloads)

Installation:
The installation is smooth: it gets recognized as "RP45-SHOPPE" and installs without glitches. I set the printer to default.

I create a text file on the desktop using "sudo nano -w test.txt" and type a few lines and save

I then try to print the file from the terminal using

```
lpr test.txt
```

The problem is that it prints the first line and stops. And this is the problem whatever I try to print - including the test page that I try to run from the CUPS server (localhost:631)

Would someone be willing to guide me out ?

---

### Post by lgastmans on 2019-02-07
These are the last lines from the error log:

```

D [07/Feb/2019:16:12:51 +0530] [Client 126] CGI data ready to be sent.
D [07/Feb/2019:16:12:51 +0530] [Client 126] con->http=0x55a2c8189110
D [07/Feb/2019:16:12:51 +0530] [Client 126] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_LENGTH, data_remaining=2147483647, response=(nil)(), pipe_pid=20342, file=23
D [07/Feb/2019:16:12:51 +0530] [Client 126] Waiting for CGI data.
D [07/Feb/2019:16:12:51 +0530] [Client 126] Script header: Content-Type: text/html;charset=utf-8
D [07/Feb/2019:16:12:51 +0530] [Client 126] Script header: 
D [07/Feb/2019:16:12:51 +0530] [Client 126] Sending status 200 for CGI.
D [07/Feb/2019:16:12:51 +0530] [Client 126] cupsdSendHeader: code=200, type="(null)", auth_type=0
D [07/Feb/2019:16:12:51 +0530] [Client 126] con->http=0x55a2c8189110
D [07/Feb/2019:16:12:51 +0530] [Client 126] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_CHUNKED, data_remaining=0, response=(nil)(), pipe_pid=20342, file=23
D [07/Feb/2019:16:12:51 +0530] [Client 126] Waiting for CGI data.
D [07/Feb/2019:16:12:51 +0530] [Client 126] CGI data ready to be sent.
D [07/Feb/2019:16:12:51 +0530] [Client 126] con->http=0x55a2c8189110
D [07/Feb/2019:16:12:51 +0530] [Client 126] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_CHUNKED, data_remaining=0, response=(nil)(), pipe_pid=20342, file=23
D [07/Feb/2019:16:12:51 +0530] [Client 126] Waiting for CGI data.
D [07/Feb/2019:16:12:51 +0530] [Client 126] con->http=0x55a2c8189110
D [07/Feb/2019:16:12:51 +0530] [Client 126] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_CHUNKED, data_remaining=0, response=(nil)(), pipe_pid=20342, file=23
D [07/Feb/2019:16:12:51 +0530] [Client 126] Waiting for CGI data.
D [07/Feb/2019:16:12:51 +0530] [Client 126] CGI data ready to be sent.
D [07/Feb/2019:16:12:51 +0530] [Client 126] con->http=0x55a2c8189110
D [07/Feb/2019:16:12:51 +0530] [Client 126] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_CHUNKED, data_remaining=0, response=(nil)(), pipe_pid=20342, file=23
D [07/Feb/2019:16:12:51 +0530] [Client 126] Waiting for CGI data.
D [07/Feb/2019:16:12:51 +0530] PID 20342 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [07/Feb/2019:16:12:51 +0530] [Client 126] con->http=0x55a2c8189110
D [07/Feb/2019:16:12:51 +0530] [Client 126] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_CHUNKED, data_remaining=0, response=(nil)(), pipe_pid=20342, file=23
D [07/Feb/2019:16:12:51 +0530] [Client 126] Waiting for CGI data.
D [07/Feb/2019:16:12:51 +0530] [Client 126] CGI data ready to be sent.
D [07/Feb/2019:16:12:51 +0530] [Client 126] con->http=0x55a2c8189110
D [07/Feb/2019:16:12:51 +0530] [Client 126] cupsdWriteClient error=0, used=0, state=HTTP_STATE_POST_SEND, data_encoding=HTTP_ENCODING_CHUNKED, data_remaining=0, response=(nil)(), pipe_pid=20342, file=23
D [07/Feb/2019:16:12:51 +0530] [Client 126] Waiting for CGI data.
D [07/Feb/2019:16:12:51 +0530] [Client 126] Sending 0-length chunk.
D [07/Feb/2019:16:12:51 +0530] [Client 126] Flushing write buffer.
D [07/Feb/2019:16:12:51 +0530] [Client 126] New state is HTTP_STATE_WAITING
D [07/Feb/2019:16:12:51 +0530] [Client 126] Waiting for request.
D [07/Feb/2019:16:12:51 +0530] [Client 126] Closing because Keep-Alive is disabled.
D [07/Feb/2019:16:12:51 +0530] [Client 126] Closing connection.
D [07/Feb/2019:16:12:51 +0530] cupsdSetBusyState: newbusy="Dirty files", busy="Active clients and dirty files"
I [07/Feb/2019:16:12:51 +0530] Saving printers.conf...
I [07/Feb/2019:16:12:51 +0530] Saving subscriptions.conf...
D [07/Feb/2019:16:12:51 +0530] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
W [07/Feb/2019:16:12:51 +0530] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'HP_LaserJet_1020-Gray..\' already exists
W [07/Feb/2019:16:12:51 +0530] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'HP_LaserJet_1020-RGB..\' already exists
W [07/Feb/2019:16:12:51 +0530] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'RP45-SH0PPE-Gray..\' already exists
E [07/Feb/2019:16:23:18 +0530] [Client 26] Returning IPP client-error-bad-request for Create-Job (ipp://localhost:631/printers/RP45-SH0PPE) from localhost
W [07/Feb/2019:16:30:19 +0530] Notifier for subscription 4963 (dbus://) went away, retrying!
W [07/Feb/2019:16:30:19 +0530] Notifier for subscription 4971 (dbus://) went away, retrying!
W [07/Feb/2019:16:32:29 +0530] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'RP45-Gray..\' already exists
E [07/Feb/2019:16:43:25 +0530] [Job 463] Aborting job because it has no files.
E [07/Feb/2019:16:43:25 +0530] [Job 464] Aborting job because it has no files.
E [07/Feb/2019:16:43:25 +0530] [Job 465] Aborting job because it has no files.

```

---

### Post by lgastmans on 2019-02-14
I am stuck with the error:

> W [14/Feb/2019:17:57:17 +0530] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'TVS_RP45_SH0PPE-Gray..\' already exists

I have tried to find where the CreateProfile error is coming from, and thought it was Ghostscript, but when I uninstalled Ghostscript other error messages popped up.

I will probably have to switch to Windows, where I have tested the printer to work.

Sad, unless someone has some time to help me out...

---

### Post by him610 on 2019-02-14
You are probably missing the linefeed character at the end of each line.

Setting the appropriate -
Emulation:   ESC / POS, Esc P, IBM
and 
choosing the correct -
Driver:  Windows 95/98/ME/2000/NT4.0/ XP, Vista, Linux

should get it to print out the way you want.

Do you have it connected through a RS-232 serial port?

---

