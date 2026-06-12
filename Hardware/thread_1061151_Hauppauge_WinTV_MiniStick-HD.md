---
title: "Hauppauge WinTV MiniStick-HD"
date: 2009-02-05
forum: Hardware
---

### Post by mac-duff on 2009-02-05
Hallo,

I am trieing now for some hours already to get my new DVB-T stick to work. Sadly without success.

When I enter the command dmesg I receive following output:
[  181.756135] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 575
[  241.761149] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 834
[  361.772125] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1037
[  408.444071] usb 5-2: new high speed USB device using ehci_hcd and address 4
[  408.578564] usb 5-2: configuration #1 chosen from 1 choice
[  408.855715] firmware: requesting sms1xxx-hcw-55xxx-dvbt-01.fw
[  408.867352] smscore_set_device_mode: error -2 loading firmware: sms1xxx-hcw-55xxx-dvbt-01.fw, trying again with default firmware
[  408.867373] firmware: requesting dvb_nova_12mhz_b0.inp
[  408.874758] smscore_set_device_mode: error -2 loading firmware: dvb_nova_12mhz_b0.inp
[  408.874779] smsusb_init_device: line: 373: smscore_start_device(...) failed
[  408.874912] smsusb_onresponse: line: 65: error, urb status -2, 0 bytes

Can please somebody help me with that?

Thx
Stephan

Edit:
Link for firmware:
[http://www.steventoth.net/linux/sms1xxx/](http://www.steventoth.net/linux/sms1xxx/)

---

### Post by mac-duff on 2009-02-05
now I copied a old firmware in the lib/firmware folder: sms1xxx-hcw-55xxx-dvbt-01.fw and now it finds a device, but still no real function.

In Kaffeine I dont find any stations.

here a log:
[ 6484.853372] usb 1-2: USB disconnect, address 9
[ 6487.517123] usb 1-2: new high speed USB device using ehci_hcd and address 10
[ 6487.650766] usb 1-2: configuration #1 chosen from 1 choice
[ 6487.656590] firmware: requesting sms1xxx-hcw-55xxx-dvbt-01.fw
[ 6488.332158] smscore_set_device_mode: firmware download success: sms1xxx-hcw-55xxx-dvbt-01.fw
[ 6488.332569] DVB: registering new adapter (Hauppauge WinTV MiniStick)
[ 6488.333362] DVB: registering frontend 0 (Siano Mobile Digital SMS1xxx)...
[ 6503.552204] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 912
[ 6623.565161] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 749
[ 6690.577974] DVB: frontend 0 frequency 874000000 out of range (44250000..867250000)
[ 6691.079801] DVB: frontend 0 frequency 882000000 out of range (44250000..867250000)
[ 6691.581392] DVB: frontend 0 frequency 890000000 out of range (44250000..867250000)
[ 6692.082772] DVB: frontend 0 frequency 898000000 out of range (44250000..867250000)
[ 6743.580170] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 945
[ 6863.597150] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 742
[ 6983.612162] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 667
[ 7066.647050] DVB: frontend 0 frequency 873833000 out of range (44250000..867250000)
[ 7067.148916] DVB: frontend 0 frequency 874000000 out of range (44250000..867250000)
[ 7067.650425] DVB: frontend 0 frequency 874167000 out of range (44250000..867250000)
[ 7068.151927] DVB: frontend 0 frequency 881833000 out of range (44250000..867250000)
[ 7068.653479] DVB: frontend 0 frequency 882000000 out of range (44250000..867250000)
[ 7069.154993] DVB: frontend 0 frequency 882167000 out of range (44250000..867250000)
[ 7069.656564] DVB: frontend 0 frequency 889833000 out of range (44250000..867250000)
[ 7070.158451] DVB: frontend 0 frequency 890000000 out of range (44250000..867250000)
[ 7070.659843] DVB: frontend 0 frequency 890167000 out of range (44250000..867250000)
[ 7071.161289] DVB: frontend 0 frequency 897833000 out of range (44250000..867250000)
[ 7071.662787] DVB: frontend 0 frequency 898000000 out of range (44250000..867250000)
[ 7072.164367] DVB: frontend 0 frequency 898167000 out of range (44250000..867250000)
[ 7103.629162] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 784
[ 7223.644170] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 749
[ 7265.776621] DVB: frontend 0 frequency 0 out of range (44250000..867250000)
[ 7343.648159] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 828
[ 7451.133529] smsusb_onresponse: line: 65: error, urb status -71, 0 bytes
[ 7451.133664] usb 1-2: USB disconnect, address 10
[ 7451.133730] smsusb_onresponse: line: 65: error, urb status -108, 0 bytes
[ 7451.133746] smsusb_onresponse: line: 65: error, urb status -108, 0 bytes
[ 7451.133759] smsusb_onresponse: line: 65: error, urb status -108, 0 bytes
[ 7451.133773] smsusb_onresponse: line: 65: error, urb status -108, 0 bytes
[ 7451.133786] smsusb_onresponse: line: 65: error, urb status -108, 0 bytes
[ 7451.133799] smsusb_onresponse: line: 65: error, urb status -108, 0 bytes
[ 7451.133813] smsusb_onresponse: line: 65: error, urb status -108, 0 bytes
[ 7451.133826] smsusb_onresponse: line: 65: error, urb status -108, 0 bytes
[ 7451.133840] smsusb_onresponse: line: 65: error, urb status -108, 0 bytes
[ 7455.172590] usb 1-2: new high speed USB device using ehci_hcd and address 11
[ 7455.305542] usb 1-2: configuration #1 chosen from 1 choice
[ 7455.312544] firmware: requesting sms1xxx-hcw-55xxx-dvbt-01.fw
[ 7455.955062] smscore_set_device_mode: firmware download success: sms1xxx-hcw-55xxx-dvbt-01.fw
[ 7455.955357] DVB: registering new adapter (Hauppauge WinTV MiniStick)
[ 7455.956140] DVB: registering frontend 0 (Siano Mobile Digital SMS1xxx)...
[ 7463.652143] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 828

---

### Post by mac-duff on 2009-02-06
now I tried it at work and I find channel, so i guess the problem is the bad connection :(

---

### Post by mac-duff on 2009-02-15
Hey again,
I figured out a new problem with Kaffeine. Its crashes a lot and sadly in the terminal is not really something exiting:

kaffeine
/dev/dvb/adapter0/frontend0 : opened ( Siano Mobile Digital SMS1xxx )
0 EPG plugins loaded for device 0:0.
Loaded epg data : 2033 events (17 msecs)
esther@mdl:~$ Tuning to: laSexta / autocount: 0
DvbCam::probe(): /dev/dvb/adapter0/ca0: : No existe el fichero ó directorio
Using DVB device 0:0 "Siano Mobile Digital SMS1xxx"
tuning DVB-T to 842000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
..... LOCKED.
NOUT: 1
dvbEvents 0:0 started
Tuning delay: 504 ms
pipe opened
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
xine pipe opened /home/esther/.kaxtv.ts
Asked to stop
pipe closed
Live stopped
dvbstream::run() end
dvbEvents 0:0 ended
fdDvr closed
Frontend closed
Tuning to: Tele7 / autocount: 1
Using DVB device 0:0 "Siano Mobile Digital SMS1xxx"
tuning DVB-T to 666000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
.... LOCKED.
NOUT: 1
dvbEvents 0:0 started
Tuning delay: 405 ms

Has maybe someone of u an idea? and how can I can my USB STick to work in MythTV?
Thx

---

### Post by mac-duff on 2009-07-02
Hi,
another problem :)

When I use Ubuntu and then plug in my USB WInTV stick everything works fine but when I let it connected and reboot it will not be recognized :(

any ideas?

---

### Post by Morraya on 2009-08-14
Hello, I have this ministick and doesn´t work in ubuntu 9.04.
Any help?

Thanks :)

---

### Post by Morraya on 2009-08-15
Ok, works!
With the firmware and new version of Me-TV.

Regards

---

### Post by gdu on 2010-02-19
Hi !

I'm using ubuntu 9.10 karmic koala and trying to make my hauppauge wintv ministick-hd (model 1247) work on it... without success...

lsusb gives : 
Bus 002 Device 004: ID 2040:c000 Hauppauge 
(which seems fine) but dmesg only
[  162.352164] usb 2-2: new high speed USB device using ehci_hcd and address 3
[  162.486184] usb 2-2: configuration #1 chosen from 1 choice
and nothing else when I plug in the device.

I added copies of all firmwares found at [http://www.steventoth.net/linux/sms1xxx/](http://www.steventoth.net/linux/sms1xxx/) (especially sms1xxx-hcw-55xxx-dvbt-02.fw that seems to be the useful one) in my /lib/firmware/ and /lib/firmware/<current-kernel-file>/.

At this stage, me-tv still ask for a dvb device...

Thanks for your help !

---

### Post by rolfsorensen on 2010-02-23
Hi.

I have the same problem with Haupage WinTV Ministick model no. 1254.
Ubuntu 9.10 kernel 2.6.31.19.

I copy the firmware  sms1xxx-hcw-55xxx-dvbt-02.fw to lib/firmware.
When I run w-scan it i get:

main:2898: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

I've tried Me-TV, Myth TV and VLC without succes.
I've crawled the web for hours, but can't find anything useful.
Do I need to load a driver, and if I do where do I get it?

I had hoped to use it for at Mythbuntu media center, but get the same results there.

Thanks in advance.

---

### Post by gdu on 2010-10-11
Hi,

I finally got it to work in Ubuntu 10.04 (2.6.32-25). Here is the way I proceeded:

- following [http://ubuconf.buron.eu/2010/03/changing-firmware-for-hauppage-wintv.html](http://ubuconf.buron.eu/2010/03/changing-firmware-for-hauppage-wintv.html) (note this is based on [http://contribs.martymac.org/FreeBSD-siano/README](http://contribs.martymac.org/FreeBSD-siano/README) that also tells you how to scan for channels, watch them,...) :
  * Download [http://www.wintvcd.co.uk/drivers/WinTV-MiniStick_4_2_26_28027_WHQL.zip](http://www.wintvcd.co.uk/drivers/WinTV-MiniStick_4_2_26_28027_WHQL.zip) (available from www.hauppauge.co.uk>support>wintv_ministick_(120xxx) )
  * Extract driver17/hcw17dvb.1b0
  * Rename it sms1xxx-hcw-55xxx-dvbt-02.fw
* Copy it in  /lib/firmware/

- Plug in your device, "dmesg | tail" gives something similar to:
[ 3921.000072] usb 2-2: new high speed USB device using ehci_hcd and address 2
[ 3921.151237] usb 2-2: configuration #1 chosen from 1 choice
[ 3921.211080] usb 2-2: firmware: requesting sms1xxx-hcw-55xxx-dvbt-02.fw
[ 3921.800072] smscore_set_device_mode: firmware download success: sms1xxx-hcw-55xxx-dvbt-02.fw
[ 3921.846109] DVB: registering new adapter (Hauppauge WinTV MiniStick)
[ 3921.847707] DVB: registering adapter 0 frontend 0 (Siano Mobile Digital MDTV Receiver)...
[ 3921.848958] usbcore: registered new interface driver smsusb


- Install Me-TV and run it
- Scan for channels using an initial file corresponding to your location from /usr/share/dvb/dvb-t/ (these files can also be generated by w_scan (w-scan package) as explained in the README previously mentioned)

For me it did the job, hoop it will help...

---

### Post by poulanker on 2010-10-20
Thanks a lot gdu :)
That trick with extracting, renaming and copying the driver did the job for me.
Excellent work, you helped me a lot.

regards Poul Anker

---

### Post by mezcalsonics on 2011-08-03
Many thanks [gdu]("http://ubuntuforums.org/member.php?u=1021469");

Fantastic instructions - relatively new to linux & these were concise & accurate. 

Works great with BackTrack v5 to BTW...

Mez

> **gdu said:**
> Hi,

I finally got it to work in Ubuntu 10.04 (2.6.32-25). Here is the way I proceeded:

- following [http://ubuconf.buron.eu/2010/03/changing-firmware-for-hauppage-wintv.html](http://ubuconf.buron.eu/2010/03/changing-firmware-for-hauppage-wintv.html) (note this is based on [http://contribs.martymac.org/FreeBSD-siano/README](http://contribs.martymac.org/FreeBSD-siano/README) that also tells you how to scan for channels, watch them,...) :
  * Download [http://www.wintvcd.co.uk/drivers/WinTV-MiniStick_4_2_26_28027_WHQL.zip](http://www.wintvcd.co.uk/drivers/WinTV-MiniStick_4_2_26_28027_WHQL.zip) (available from www.hauppauge.co.uk>support>wintv_ministick_(120xxx) )
  * Extract driver17/hcw17dvb.1b0
  * Rename it sms1xxx-hcw-55xxx-dvbt-02.fw
* Copy it in  /lib/firmware/

- Plug in your device, "dmesg | tail" gives something similar to:
[ 3921.000072] usb 2-2: new high speed USB device using ehci_hcd and address 2
[ 3921.151237] usb 2-2: configuration #1 chosen from 1 choice
[ 3921.211080] usb 2-2: firmware: requesting sms1xxx-hcw-55xxx-dvbt-02.fw
[ 3921.800072] smscore_set_device_mode: firmware download success: sms1xxx-hcw-55xxx-dvbt-02.fw
[ 3921.846109] DVB: registering new adapter (Hauppauge WinTV MiniStick)
[ 3921.847707] DVB: registering adapter 0 frontend 0 (Siano Mobile Digital MDTV Receiver)...
[ 3921.848958] usbcore: registered new interface driver smsusb


- Install Me-TV and run it
- Scan for channels using an initial file corresponding to your location from /usr/share/dvb/dvb-t/ (these files can also be generated by w_scan (w-scan package) as explained in the README previously mentioned)

For me it did the job, hoop it will help...

---

### Post by tommpogg on 2013-01-08
The solution proposed by gdu in the post #10 worked for me too.
Thanks.

By the way, I am using Xubuntu 12.10

---

### Post by xxilinxx on 2013-01-22
Hi guys,

looking around I found a new version of the firmware.

Follow the procedure illustrated by gdu, but instead of using the suggested firmware use the one available with the last version of WinTV (2.6d).

Install WinTV on a Windows OS and copy the following file:
C:\WINDOWS\system32\drivers\hcw17dvb.1b0
(I installed it in Windows XP, but it is similar for other windows versions)

This is the version of the firmware updated to 2011.
At the moment I don't know what improvements you get with the new version...

Just a question: using femon -H (the utility in dvb-apps to check the signal) I see that every channel has a signal strength of 0% and this is obviously an error. 
Any suggestion?

Cheers

---

