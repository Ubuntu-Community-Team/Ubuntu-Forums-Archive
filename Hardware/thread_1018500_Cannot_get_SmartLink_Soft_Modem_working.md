---
title: "Cannot get SmartLink Soft Modem working"
date: 2008-12-22
forum: Hardware
---

### Post by imbuto on 2008-12-22
Hi all!

I need a little help to get my soft modem working! Yeah, I need to use dial-up... back to my home town there's no other kind of connectivity, so my Linux laptop is now offline. Luckily (?) I didn't uninstall Windoz yet so I can still post.

So... let's get started:
```

#~ Cygwin
wget [http://132.68.73.235/linmodems/packages/scanModem.gz](http://132.68.73.235/linmodems/packages/scanModem.gz)

```

After rebooting into Linux:
```

cd tmp/modem
gzip -d scanModem.gz
chmod 777 scanModem
./scanModem

```
Ok, modem is there and seems to be recognized properly:
```

#~ card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
#~ 00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
#~ Codec: Motorola Si3054

```
So I type:
```

sudo slmodemd -country=ITALY --alsa hw:0,6
#~ SmartLink Soft Modem: version 2.9.9e-pre1 Sep 30 2007 00:07:03
#~ symbolic link `/dev/ttySL0' -> `/dev/pts/2' created.
#~ modem `hw:0,6' created. TTY is `/dev/pts/2'
#~ Use `/dev/ttySL0' as modem device, Ctrl+C for termination.

```
Open another terminal window and:
```

sudo wvdialconf /etc/wvdial.conf
#~ Scanning your serial ports for a modem.

#~ Modem Port Scan<*1>: S0   S1   S2   S3
#~ WvModem<*1>: Cannot get information for serial port.
#~ ttySL0<*1>: ATQ0 V1 E1 -- OK
#~ ttySL0<*1>: ATQ0 V1 E1 Z -- OK
#~ ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
#~ ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
#~ ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
#~ ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
#~ ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
#~ ttySL0<*1>: Speed 4800: AT -- OK
#~ ttySL0<*1>: Speed 9600: AT -- OK
#~ ttySL0<*1>: Speed 19200: AT -- OK
#~ ttySL0<*1>: Speed 38400: AT -- OK
#~ ttySL0<*1>: Speed 57600: AT -- OK
#~ ttySL0<*1>: Speed 115200: AT -- OK
#~ ttySL0<*1>: Speed 230400: AT -- OK
#~ ttySL0<*1>: Speed 460800: AT -- OK
#~ ttySL0<*1>: Max speed is 460800; that should be safe.
#~ ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

#~ Found a modem on /dev/ttySL0.
#~ Modem configuration written to /etc/wvdial.conf.
#~ ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```
I edit the configuration files inserting my ISP account data:
vim /etc/wvdial.conf

The files now looks like this:
```

[Dialer Defaults]
Init1 = ATZ
Carrier Check = no
Modem Type = Analog Modem
ISDN = 0
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Password = nobodyknowsit
New PPPD = yes
Phone = 1234560000
Modem = /dev/ttySL0
Username = myself
Baud = 460800

```
Fine, let's try it:
```

wvdial
#~ --> WvDial: Internet dialer version 1.60
#~ --> Cannot get information for serial port.
#~ --> Initializing modem.
#~ --> Sending: ATZ
#~ ATZ
#~ OK
#~ --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#~ ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#~ OK
#~ --> Modem initialized.
#~ --> Sending: ATDT1234560000
#~ --> Waiting for carrier.
#~ ATDT1234560000
#~ NO CARRIER
#~ ERROR
#~ --> No Carrier!  Trying again.
#~ --> Sending: ATDT1234560000
#~ --> Waiting for carrier.
#~ ATDT1234560000
#~ NO CARRIER
#~ (looping forever)

```
And on the daemon side:
```

#~ error: period size 48 is not supported by playback (64).
#~ (looping forever)

```
Ok, it does not work. Let's check the slmodemd version:
```

slmodemd --version
#~ SmartLink Soft Modem: version 2.9.9e-pre1 Sep 30 2007 00:07:03

```
I try downloading  slmodem-2.9.11-20080817.tar.gz and the patch I found for the error, slmodem-2.9.11-alsa-period-size.patch, which is however no longer necessary
```

tar xfz slmodem-2.9.11-20080817.tar.gz
cd slmodem-2.9.11-20080817/
patch -p1 < ../slmodem-2.9.11-alsa-period-size.patch
#~ Reversed (or previously applied) patch detected!  Assume -R? [n] n
#~ Apply anyway? [n] n
#~ Skipping patch.
#~ 1 out of 1 hunk ignored -- saving rejects to file modem/modem_main.c.rej

```
Then, enable ALSA support by uncommenting the line SUPPORT_ALSA:=1 in modem/Makefile and:
```

make
#~ make -C modem all
#~ make[1]: Entering directory `/home/mauro/tmp/modem/slmodem-2.9.11-20080817/modem'
#~ rebuild profile...
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_main.o -c modem_main.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_cmdline.o -c modem_cmdline.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_datafile.o -c modem_datafile.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_at.o -c modem_at.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_timer.o -c modem_timer.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_pack.o -c modem_pack.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_ec.o -c modem_ec.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_comp.o -c modem_comp.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_param.o -c modem_param.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_debug.o -c modem_debug.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o homolog_data.o -c homolog_data.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_sinus.o -c dp_sinus.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_dummy.o -c dp_dummy.c
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o sysdep_common.o -c sysdep_common.c
#~ gcc -o slmodemd modem_main.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
#~ gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_test.o -c modem_test.c
#~ gcc -o modem_test modem_test.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
#~ make[1]: Leaving directory `/home/mauro/tmp/modem/slmodem-2.9.11-20080817/modem'
#~ make -C drivers KERNEL_DIR=/lib/modules/2.6.24-22-generic/build
#~ make[1]: Entering directory `/home/mauro/tmp/modem/slmodem-2.9.11-20080817/drivers'
#~ doing kernel-ver::
#~ cc -I/lib/modules/2.6.24-22-generic/build/include -o kernel-ver kernel-ver.c
#~ kernel-ver.c:9:30: error: linux/utsrelease.h: No such file or directory
#~ kernel-ver.c: In function â€˜mainâ€™:
#~ kernel-ver.c:14: error: â€˜UTS_RELEASEâ€™ undeclared (first use in this function)
#~ kernel-ver.c:14: error: (Each undeclared identifier is reported only once
#~ kernel-ver.c:14: error: for each function it appears in.)
#~ make[1]: *** [kernel-ver] Error 1
#~ make[1]: Leaving directory `/home/mauro/tmp/modem/slmodem-2.9.11-20080817/drivers'
#~ make: *** [drivers] Error 2

```
Why?? Ok, let's try with the precompiled version.

I download SLMODEMD_gcc4.2_alsa1.0.17.tar.gz and:
```

tar xzf SLMODEMD_gcc4.2_alsa1.0.17.tar.gz
sudo ./setup
slmodemd --version
#~ SmartLink Soft Modem: version 2.9.11 Dec 16 2008 22:54:51

```
Run wvdial and:
```

#~ --> WvDial: Internet dialer version 1.60
#~ --> Cannot get information for serial port.
#~ --> Initializing modem.
#~ --> Sending: ATZ
#~ ATZ
#~ OK
#~ --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#~ ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#~ OK
#~ --> Modem initialized.
#~ --> Sending: ATDT1234560000
#~ --> Waiting for carrier.
#~ ATDT1234560000
#~ NO DIALTONE
#~ --> No dial tone.
#~ --> Disconnecting at Mon Dec 22 11:39:14 2008

```
At least no daemon error is shown, but still nothing.
Now I've really run out of ideas.
I do not understand why, if I say Carrier Check = no, it still says waiting for carrier.
And I do not understand what No dial tone means.
Is there anybody out there who can help me? I'd like to put the flag [SOLVED] once!

Cheers!

Ubuntu: Linux for human beings.
I thought I was a human being, but I am not sure any more.

---

### Post by imbuto on 2008-12-22
Making progress. Slowly.

The no dial tone error message is probably due to a non standard dial tone used in my country. Hence the modem does not recognize it. Issuing an ATX3 should disable the dial tone check.
So, I replaced the Init2 line in wvdial.conf:
```

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

```
with:
```

Init2 = ATQ0 X3 V1 E1 S0=0 &C1 &D2 +FCLASS=0

```
No more dial tone messages, but again waiting for carrier. But I specified no carrier check! I tried also issuing a ATX0 command before the dial, which should disable the carrier sensing, but no result (waiting for carrier is still there).
```

sudo wvdial
#~ --> WvDial: Internet dialer version 1.60
#~ --> Cannot get information for serial port.
#~ --> Initializing modem.
#~ --> Sending: ATZ
#~ ATZ
#~ OK
#~ --> Sending: ATQ0 X3 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#~ ATQ0 X3 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#~ OK
#~ --> Modem initialized.
#~ --> Sending: ATDT1234560000
#~ --> Waiting for carrier.
#~ ATDT1234560000
#~ NO CARRIER
#~ --> No Carrier!  Trying again.
#~ --> Sending: ATDT1234560000
#~ --> Waiting for carrier.
#~ ATDT1234560000
#~ NO CARRIER
#~ --> No Carrier!  Trying again.
#~ --> Maximum Attempts Exceeded..Aborting!!
#~ --> Disconnecting at Mon Dec 22 15:14:13 2008

```
Any suggestion is welcome! Analog modems are disappearing, you won't have many other chances to give support on the topic! Hurry up before I find the solution by myself! ;)

Btw if this can be of any help,
```

uname -a
#~ Linux my-laptop 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux
alsactl --version
#~ alsactl version 1.0.15

```

---

### Post by imbuto on 2008-12-23
Some material on the topic from linmodems.org
RE: Motorola Si3054 - No Carrier Error: [http://linmodems.org/cgi-bin/ezmlm-cgi?1:mss:32391:200811:nhbiodemhkchjmmbgomc](http://linmodems.org/cgi-bin/ezmlm-cgi?1:mss:32391:200811:nhbiodemhkchjmmbgomc)

Other Init2 string I tried
```

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 +MS=90
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 +MS=34

```
which should help in case of lines with weak signal (if I got it right).

I also found out that the X3 command can be replaced by:
```

Abort on No Dialtone = off

```
in the wvdial.conf
But, still nothing. No carrier.

---

### Post by _duncan_ on 2008-12-24
Been a while since I worked with smartlink modems. If memory serves, you also need to set```
Stupid Mode = yes
``` in /etc/wvdial.conf.

---

### Post by imbuto on 2008-12-24
Thanks for the tip. Unfortunately I already tried that without success, both specifying "on" and "yes" (I forgot to mention it).

---

### Post by _duncan_ on 2008-12-24
Can you post the content of the file /etc/wvdial.conf? Just make sure to edit out your login info before posting for security reasons.

-----------------

Also, please check if the file /etc/resolv.conf exists in your system. If not, please run the following command in the terminal:
```
sudo touch /etc/resolv.conf
```

This will create a blank /etc/resolv.conf if it's not present. Afterwards, try dialing out again and see if it makes a difference. The lack of the /etc/resolv.conf file used to be a problem with wvdial in earlier versions of Ubuntu. Not sure if it's still an issue with more recent releases.

-----------------

BTW, you forgot to read the fine print: Ubuntu is linux for human beings with broadband, hahaha. At least I used to feel that way when I was struggling with dial-up 3 years ago. Took me 3 months of poking around before finally getting connected. Just hang in there.

---

### Post by imbuto on 2008-12-26
File /etc/resolv.conf exists with the following content:
```

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5319
#
### END INFO



nameserver 10.0.0.1

```

Regarding the wvdial.conf, I tried several combinations of options ad initialization strings, starting from the default file generated by wvdialconf:
```

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Username = <Your Login Name>
Init1 = ATZ
; Password = <Your Password>
Modem = /dev/ttySL0
Baud = 460800

```
My current /etc/wvdial.conf looks like this:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 X3 V1 E1 S0=0 &C1 &D2 +FCLASS=0 +MS=34
Abort on No Dialtone = off
Carrier Check = off
Stupid Mode = yes
Modem Type = Analog Modem
ISDN = 0
New PPPD = on
Phone = 7027020000
Modem = /dev/modem
Username = ?????????
Password = ?????????
Baud = 57600
Dial Attempts = 1
Dial Command = ATDT

```

I tried to get some more info from slmodemd, starting it as:
```

slmodemd -country=ITALY --alsa --debug=2 hw:0,6

```
Now at least I know that there is a difference if I unplug the modem cord.
With those command line options, I get this output (I removed part of it and replaced with dots, where repeated lines or long sequence of characters appeared, to make it smaller... also because I don't know what's behind those strange sequences - my account data maybe -)
```

<313.739324> SmartLink Soft Modem: version 2.9.11 Dec 16 2008 22:54:51
<313.739364> hw:0,6: startup modem...
<313.739416> hw:0,6: update termios...
symbolic link `/dev/ttySL0' -> `/dev/pts/3' created.
modem `hw:0,6' created. TTY is `/dev/pts/3'
<313.739774> open file: /var/lib/slmodem/data.hw:0,6...
<313.740722> main: rt applyed: SCHED_FIFO, pri 99
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
<345.232873> main: termios changed.
<345.232919> hw:0,6: update termios...
<345.293175> main: termios changed.
<345.293201> hw:0,6: update termios...
<345.392120> hw:0,6: run cmd: ATZ
<345.392148> hw:0,6: modem reset...
<345.392156> hw:0,6: modem set state: 1 --> 1...
<345.392166> hw:0,6: modem set mode: -> 0...
<345.392173> hw:0,6: modem report result: 0 (OK)
<345.492468> hw:0,6: run cmd: ATQ0X3V1E1S0=0&C1&D2+FCLASS=0+MS=34
<345.492520> hw:0,6: modem set mode: -> 0...
<345.492535> hw:0,6: modem report result: 0 (OK)
<345.592268> hw:0,6: run cmd: ATDT7027020000
<345.592292> hw:0,6: modem dial: T7027020000...
<345.592297> hw:0,6: modem_dial_start...
<345.592302> call: create...
<345.592309> CallProgFP_Create >>
<345.592313> APPLY_FILTER = 0
<345.592325> Detection Thresholds: levle_fix=40,--> LEVEL_THRESHOLD=102
<345.592330> ============> 0
<345.592334> Cadence: Busy Tone loose detection is 0
<345.592338> TYPE BUSY
<345.592342> Filter index 0
<345.592345> Filter SubIndex 0
<345.592349> MAX_ON_TIME 27 Buffers     MIN_ON_TIME 10 Buffers
<345.592353> MAX_OFF_TIME 27 Buffers    MIN_OFF_TIME 10 Buffers
<345.592357> OFF_TIME_THAT_RESETS_CYCLE 81
<345.592361> BUFFER LENGTH 160 samples.
<345.592364> INTEGRATION_LENGTH 0[ms]
<345.592368> LEVEL 102
<345.592373> INTEGRATION_TIME = 0 Buffers.
<345.592377> Detection Thresholds: levle_fix=40,--> LEVEL_THRESHOLD=102
<345.592382> TYPE DIAL
<345.592385> Filter index 4
<345.592389> Filter SubIndex 0
<345.592392> MAX_ON_TIME 0 Buffers     MIN_ON_TIME 0 Buffers
<345.592396> MAX_OFF_TIME 0 Buffers    MIN_OFF_TIME 0 Buffers
<345.592400> OFF_TIME_THAT_RESETS_CYCLE 0
<345.592404> BUFFER LENGTH 666 samples.
<345.592407> INTEGRATION_LENGTH 1500[ms]
<345.592411> LEVEL 102
<345.592415> INTEGRATION_TIME = 16 Buffers.
<345.592420> CALLPROG Create <<
<345.592424> CALLPROG Dialing T7027020000
<345.592428> Configuration->tone_DigitLength 100
<345.592432> Configuration->pulse_OffHookTime 41
<345.592436> Configuration->pulse_OnHookTime 65
<345.592440> Configuration->dialPauseTime 2
<345.592443> Configuration->flashTime 11
<345.592447> Configuration->toneOrPulseFlag 0
<345.592451> Configuration->dialModifierValidationFlag 1
<345.592455> Configuration->ABCD_PermittedFlag 0
<345.592459> Configuration->pulseAndToneInSameStringPermittedFlag 0
<345.592463> Configuration->callingToneFlag 0
<345.592467> Configuration->commaPauseDurLimit 30
<345.592470> Configuration->digitPattern 1
<345.592474> Configuration->tone_BetweenDigitsInterval 100
<345.592478> Configuration->pulse_BetweenDigitsInterval 800
<345.592482> DTMF_Gain1 = 10337
<345.592486> DTMF_Gain2 = 13014
<345.592490> AnalyzeDialString: Updated 17 May 1999 00:50
<345.592494> AnalyzeDialString: LAST_DIALABLE_SYMBOL is 10
<345.592498> Dial String Syntax is VALID
<345.592503> GetNoAnswerTimeOut. 60
<345.592507> BlindCall: GetBlindDialPause = 2 .
<345.592511> CALLPROG_Dial was exited.
<345.592514> call: create RC: 9600 <-> 8000...
<345.592520> hw:0,6: modem_start..
<345.592524> hw:0,6: modem set state: 1 --> 2...
<345.592528> hw:0,6: new state: DP_ESTAB
<345.592533> main: alsa_ioctl: cmd 8, arg 3...
<345.592537> hw:0,6: modem set hook: 0 --> 1...
<345.592541> main: alsa_ioctl: cmd 2, arg 1...
<345.592655> main: alsa_ioctl: cmd 11, arg 0...
<345.592696> main: alsa_ioctl: cmd 4, arg 2580...
<345.592701> main: alsa_ioctl: cmd 7, arg 30...
<345.592706> main: alsa_start...
Hardware PCM card 0 'HDA Intel' device 6 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 9600
  exact rate   : 9600 (9600/1)
  msbits       : 16
  buffer_size  : 2048
  period_size  : 64
  period_time  : 6666
  tick_time    : 0
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 64
  xfer_align   : 4
  start_threshold  : 2147483647
  stop_threshold   : 2048
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Hardware PCM card 0 'HDA Intel' device 6 subdevice 0
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 9600
  exact rate   : 9600 (9600/1)
  msbits       : 16
  buffer_size  : 2048
  period_size  : 64
  period_time  : 6666
  tick_time    : 0
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 64
  xfer_align   : 4
  start_threshold  : 2147483647
  stop_threshold   : 2048
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
<345.625169> main: startup write: 384...
<345.638476> call: process: msg 18 --> 0
<347.238441> DCR: initial DC Evaluation done, DC level -137, enabled
<347.638460> CALLPROG: Time out
<347.638505> STATE:  CALLPROG_WAIT_DIAL --> CALLPROG_DIALING
<347.638528> call: process: msg 0 --> 3
<347.638548> DIALER_INITIAL_STATE
<347.638559> Digit is T
<347.638569> Dialer.c: GetNextDigit... TONE_OR_PULSE_FLAG became TONE_DIALING
<347.638580> Digit is 7
<347.638590> Samples left = 800
<347.638615> call: process: msg 3 --> 0
<347.731786> Done Generating digit
<347.831794> Done Generating silence between digits
...
<349.431825> Samples left = 800
<349.538444> Done Generating digit
<349.538481> DIALER_END_STATE
<349.538493> STATE:  CALLPROG_DIALING --> CALLPROG_WAIT_RING
<349.538513> call: process: msg 0 --> 4
<349.551780> call: process: msg 4 --> 0
<351.325122> Found 2100
<351.325174> call: process: msg 0 --> 16
<351.325188> hw:0,6: 54656: change dp: --> 8...
<351.325201> v8: create: caller 1, automode 0, dp id 34.
<351.325217> V8: Create called, V8 version 23/09/03 .
<351.325227> ############################################################
<351.325237> V8: local configuration :
<351.325247> 	Side = Caller
<351.325256> 	Operation Mode = 0
<351.325266> 	Modulations - V90=0, V34=1, V34HD=0, V32=1, V22=0, V17=0, V29=0, V27=0, V23=0, V21=0
<351.325280> 	Call Functions - Data=1, CallRxFax=0, CallTxFax=0, V.80=0
<351.325292> 	Protocol - LAPM V.42
<351.325302> 	v8bisIndication - 0
<351.325311> 	timeouts - signal detect 12 sec, message detect 7 sec
<351.325323> 	quickConnectEnabled - 0
<351.325332> 	lapmIndication - 1
<351.325342> 	ucodeForQts - 9
<351.325352> 	ansPcmLevel - 0
<351.325361> ############################################################
<351.325378> V8: Initial CM message length is 8 octets
<351.325389> call: delete...
<351.325399> Dialer was aborted.
<351.325408> CALLPROG_Delete is entered
<351.325418> cadence_delete with CADENCE_DIAL_OBJ is invoked
<351.325429> cadence_delete with CADENCE_OBJ is invoked
<351.325439> CALLPROG_Delete is exited
<351.338445> V8: State changed from V8_INIT to V8_ORG_WAITING_FOR_ANSAM
<351.338466> v8: status (6) V8_ORG_WAITING_FOR_ANSAM
<351.418421> V8: State changed from V8_ORG_WAITING_FOR_ANSAM to V8_ORG_ANSAM_DETECTED_WAITING_TE
<351.418444> v8: status (7) V8_ORG_ANSAM_DETECTED_WAITING_TE
<352.071771> ANSAM phase reversals detected delay = 449
<352.071822> ANSAM phase reversals detected delay = 449
<352.071833> ANSAM phase reversals detected delay = 449
<352.411751> V8 ANSAM Detected (CM ready)
<352.411798> V8: State changed from V8_ORG_ANSAM_DETECTED_WAITING_TE to V8_ORG_SEND_CM
<352.411813> v8: status (8) V8_ORG_SEND_CM
<353.991736> V8: on CALLER: remote call function is: 107
<353.991783> V8: call function DATA indication...
<353.991796> V8: Got Call Function Match!
<354.018420> V8: State changed from V8_ORG_SEND_CM to V8_ORG_SEND_CJ
<354.018449> v8: status (10) V8_ORG_SEND_CJ
<354.118433> V8: State changed from V8_ORG_SEND_CJ to V8_OK
<354.118454> v8: process: OK.
<354.118465> V8Report: remote V90: mod - 0, digital connection - 1, pcmIndication - 0
<354.118477> V8Report: v90:0, v34:1, v34hd:0, V32:1, V22:0, V17:0, V29:0, V27:0, V23:0, V21:0
<354.118492> main: alsa_ioctl: cmd 10, arg 0...
<354.118503> main: delay = 424
<354.118514> v8: Link established. Idle timer 1096.
<354.118524> v8: status (13) V8_OK
<354.118535> hw:0,6: 81472: change dp: --> 34...
<354.118548> vpcm: create: dp 34, caller 1, frag 48 (size 53848).
<354.118815> VPCMXF_Create: side is Analog, maxDataBuffer - 48
<354.118834> V90Modem Construction (as Analog Modem)
<354.118881> $!$
...
<354.118965> *********************************************************
<354.118975> V90Modem Version: 2.98  (25-Mar-04)
<354.118986> *********************************************************
<354.119006> $!$ ...
<354.119049> $!$ ...
<354.119084> *********************************************************
<354.119096> V90Parameters: upStream min rate : 4800 upStream max rate : 4800  Rate mask :1
<354.119123> $!$ ...
<354.119147> $!$ ...
<354.119175> $!$ ...
<354.119218> $!$ ...
<354.120214> V90Phase3Demodulator: Reset called, sessionFlag = 1 !
<354.120239> V90Phase3Demodulator: initial state set to WaitForSd
<354.120486> $!$ ...
<354.120597> V92Modem Construction (as Analog Modem)
<354.120634> $!$ ...
<354.120758> *********************************************************
<354.120768> V92Modem Version: 1.1  (9-Apr-01)
<354.120779> *********************************************************
<354.120798> $!$ ...
<354.120825> $!$ ...
<354.120861> $!$ ...
<354.120877> V92Modulator constraction
<354.121778> $!$ ...
<354.121794> V92Modulator reset
<354.121816> V92EchoCanceller: constraction
<354.121843> $!$ ...
<354.121950> vpcm: VPCM rate limits: 300-56000
<354.121961> main: alsa_ioctl: cmd 10, arg 0...
<354.121972> main: delay = 424
<354.121982> vpcm: Delays: HW 244, DMA 580
<354.121992> vpcm: initial dp V.34, session type 0.
<354.122003> VPcmV34Create: quick connect indication from phase1 = 0
<354.122014> VPcmV34Create: Uqts index is 9
<354.122024> VPcmV34Create: ANSpcm level index is 0
<354.122034> VPcmV34Create, initial Session Type = 0
<354.122044> RX at 815D658
<354.122072> On Create: Setting desired TX MD (0 mSec)!
<354.122101> $!$ ...
<354.122112> V34SetupModulator: baudrate 2400, carrier 1800, preemp 0, V90=0. fullReset=0
<354.122129> V34SetupDemodulator: baudrate 2400, carrier 1800
<354.122141> V34SetupModulator: baudrate 600, carrier 1200, preemp 0, V90=0. fullReset=1
<354.122166> V34FLO: Echo running in Original Integer...
<354.122177> V34FLO: Echo running in Original Integer...
<354.122189> V34HSHAKE: txstate NOSTATE0=>SILENCEINFO(rx NOSTATE0, mst NOSTATE0, [1]0, [2]0)
<354.122203> V34HSHAKE: rxstate NOSTATE0=>RX_DPSK(tx SILENCEINFO, mst NOSTATE0, [1]0, [2]0)
<354.122216> V34HSHAKE: microstate NOSTATE0=>DET_SYNC(tx SILENCEINFO, rx RX_DPSK, [1]0, [2]0)
<354.122230> VPcmV34Main: minLevel given is 0 , minSigLevel set to 101
<354.122242> V34 filtdelay set to 95 (params initial delay = 244)
<354.122253> V34FEC, V34dmadelay set to 972, (ext delay=580)
<354.122280> $!$...
<354.122291> VPcmFlo: From Stream - Entrance Filter forced disabled...
<354.122303> VPcmFlo: YES! entrance filter applied = 0
<354.122314> v8: delete...
<354.125063> main: change delay -64...
<354.138362> main: change delay -120...
<354.185070> main: alsa xrun: try to recover...
<354.200069> main: alsa xrun: recovered.
<354.200101> main: dev write = 0
<354.200121> main: alsa xrun: try to recover...
<354.216069> main: alsa xrun: recovered.
<354.216106> main: dev read = 0
<354.216126> main: alsa xrun: try to recover...
<354.232079> main: alsa xrun: recovered.
<354.232148> main: dev read = 0
<354.232167> main: alsa xrun: try to recover...
<354.248062> main: alsa xrun: recovered.
<354.248079> main: dev read = 0
<354.268170> V34HSHAKE: txstate SILENCEINFO=>TX_DPSK(rx RX_DPSK, mst DET_SYNC, [1]10, [2]0)
<354.268191> setINFO0aBits - setting info0a for V.34
<354.268422> main: alsa xrun: try to recover...
<354.288077> main: alsa xrun: recovered.
<354.288093> main: dev write = 0
<354.321733> main: alsa xrun: try to recover...
<354.336063> main: alsa xrun: recovered.
<354.336080> main: dev write = 0
<354.356401> main: alsa xrun: try to recover...
<354.372048> main: alsa xrun: recovered.
<354.372065> main: dev write = 0
<354.385670> main: alsa xrun: try to recover...
<354.400040> main: alsa xrun: recovered.
<354.400061> main: dev write = 0
<354.420191> V34HSHAKE: txstate TX_DPSK=>TONE_AB(rx RX_DPSK, mst DET_SYNC, [1]0, [2]0)
<354.420378> main: alsa xrun: try to recover...
<354.436041> main: alsa xrun: recovered.
...
<355.328063> main: alsa xrun: recovered.
<355.328084> main: dev read = 0
<355.348270> VPcmV34Main: Masking CAS detection after 4832 in train...
<355.348410> main: alsa xrun: try to recover...
<355.365084> main: alsa xrun: recovered.
<355.365140> main: dev write = 0
...
<365.952116> main: alsa xrun: try to recover...
<365.968044> main: alsa xrun: recovered.
<365.968067> main: dev read = 0
<366.008187> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]0)
<366.008215> DET_SYNC is received in RX_DPSK,rx->gain=0xbe8
<366.021703> main: alsa xrun: try to recover...
<366.036038> main: alsa xrun: recovered.
<366.036059> main: dev write = 0
<366.069724> main: alsa xrun: try to recover...
<366.084038> main: alsa xrun: recovered.
<366.084071> main: dev write = 0
<366.084090> main: alsa xrun: try to recover...
<366.100041> main: alsa xrun: recovered.
<366.100094> main: dev read = 0
<366.100112> main: alsa xrun: try to recover...
<366.116044> main: alsa xrun: recovered.
<366.116058> main: dev read = 0
<366.129589> V34INFO, info0 CRC not received properly in DET_INFO
<366.129609> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<366.129786> main: alsa xrun: try to recover...
<366.144066> main: alsa xrun: recovered.
<366.144136> main: dev write = 0
<366.144155> main: alsa xrun: try to recover...
...
<366.788115> main: alsa xrun: try to recover...
<366.804063> main: alsa xrun: recovered.
<366.804083> main: dev read = 0
<366.817410> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<366.817431> DET_SYNC is received in RX_DPSK,rx->gain=0xbe5
<366.817778> main: alsa xrun: try to recover...
<366.832060> main: alsa xrun: recovered.
<366.832076> main: dev write = 0
<366.859090> main: alsa xrun: try to recover...
<366.872049> main: alsa xrun: recovered.
<366.872067> main: dev write = 0
<366.892289> V34INFO, info0 CRC not received properly in DET_INFO
<366.892309> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<366.892465> main: alsa xrun: try to recover...
<366.908061> main: alsa xrun: recovered.
<366.908076> main: dev write = 0
<366.955026> main: alsa xrun: try to recover...
<366.968040> main: alsa xrun: recovered.
<366.968062> main: dev write = 0
<367.001714> main: alsa xrun: try to recover...
<367.016064> main: alsa xrun: recovered.
<367.016083> main: dev write = 0
<367.029382> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<367.029402> DET_SYNC is received in RX_DPSK,rx->gain=0xbe4
<367.043046> main: alsa xrun: try to recover...
<367.056043> main: alsa xrun: recovered.
<367.056068> main: dev write = 0
<367.069733> main: alsa xrun: try to recover...
<367.084061> main: alsa xrun: recovered.
<367.084077> main: dev write = 0
<367.097732> main: alsa xrun: try to recover...
<367.112063> main: alsa xrun: recovered.
<367.112083> main: dev write = 0
<367.125624> V34INFO, info0 CRC not received properly in DET_INFO
<367.125642> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<367.125794> main: alsa xrun: try to recover...
<367.140061> main: alsa xrun: recovered.
<367.140077> main: dev write = 0
<367.167003> main: alsa xrun: try to recover...
<367.181068> main: alsa xrun: recovered.
<367.181103> main: dev write = 0
<367.181123> main: alsa xrun: try to recover...
<367.197056> main: alsa xrun: recovered.
<367.197086> main: dev read = 0
<367.217440> main: alsa xrun: try to recover...
<367.236081> main: alsa xrun: recovered.
<367.236109> main: dev write = 0
<367.262909> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<367.262932> DET_SYNC is received in RX_DPSK,rx->gain=0xbe3
<367.263085> main: alsa xrun: try to recover...
<367.276063> main: alsa xrun: recovered.
...
<367.376083> main: dev write = 0
<367.376102> main: alsa xrun: try to recover...
<367.392059> main: alsa xrun: recovered.
<367.392074> main: dev read = 0
<367.405501> V34INFO, info0 CRC not received properly in DET_INFO
<367.405519> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<367.425696> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<367.425716> DET_SYNC is received in RX_DPSK,rx->gain=0xbe2
<367.425792> main: alsa xrun: try to recover...
<367.440064> main: alsa xrun: recovered.
<367.440094> main: dev write = 0
...
<367.612116> main: alsa xrun: try to recover...
<367.628061> main: alsa xrun: recovered.
<367.628077> main: dev read = 0
<367.641417> V34INFO, info0 CRC not received properly in DET_INFO
<367.641435> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<367.654828> main: alsa xrun: try to recover...
<367.668047> main: alsa xrun: recovered.
<367.668054> main: dev write = 0
<367.668079> main: alsa xrun: try to recover...
...
<368.100099> main: alsa xrun: try to recover...
<368.116060> main: alsa xrun: recovered.
<368.116083> main: dev read = 0
<368.129485> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<368.129510> DET_SYNC is received in RX_DPSK,rx->gain=0xbe2
<368.129742> main: alsa xrun: try to recover...
<368.144047> main: alsa xrun: recovered.
<368.144063> main: dev write = 0
<368.164408> main: alsa xrun: try to recover...
<368.180062> main: alsa xrun: recovered.
<368.180078> main: dev write = 0
<368.180119> main: alsa xrun: try to recover...
<368.196063> main: alsa xrun: recovered.
<368.196082> main: dev read = 0
<368.216365> main: alsa xrun: try to recover...
<368.233066> main: alsa xrun: recovered.
<368.233087> main: dev write = 0
<368.246586> V34INFO, info0 CRC not received properly in DET_INFO
<368.246603> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<368.246699> main: alsa xrun: try to recover...
<368.260039> main: alsa xrun: recovered.
...
<368.586778> main: alsa xrun: try to recover...
<368.600041> main: alsa xrun: recovered.
<368.600067> main: dev write = 0
<368.606776> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<368.606807> DET_SYNC is received in RX_DPSK,rx->gain=0xa96
<368.626986> main: alsa xrun: try to recover...
<368.640062> main: alsa xrun: recovered.
<368.640080> main: dev write = 0
<368.653779> main: alsa xrun: try to recover...
<368.668106> main: alsa xrun: recovered.
<368.668131> main: dev write = 0
<368.688423> main: alsa xrun: try to recover...
<368.704039> main: alsa xrun: recovered.
<368.704105> main: dev write = 0
<368.704123> main: alsa xrun: try to recover...
<368.720046> main: alsa xrun: recovered.
<368.720062> main: dev read = 0
<368.733316> V34INFO, info0 CRC not received properly in DET_INFO
<368.733332> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<368.733693> main: alsa xrun: try to recover...
<368.748045> main: alsa xrun: recovered.
<368.748061> main: dev write = 0
...
<368.880316> main: alsa xrun: try to recover...
<368.896039> main: alsa xrun: recovered.
<368.896060> main: dev write = 0
<368.916399> main: alsa xrun: try to recover...
<368.932065> main: alsa xrun: recovered.
<368.932088> main: dev write = 0
<368.945606> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<368.945626> DET_SYNC is received in RX_DPSK,rx->gain=0xbe0
<368.945774> main: alsa xrun: try to recover...
<368.960062> main: alsa xrun: recovered.
<368.960079> main: dev write = 0
<369.000418> main: alsa xrun: try to recover...
<369.016042> main: alsa xrun: recovered.
<369.016070> main: dev write = 0
<369.029565> V34INFO, info0 CRC not received properly in DET_INFO
<369.029588> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<369.029732> main: alsa xrun: try to recover...
<369.044062> main: alsa xrun: recovered.
<369.044078> main: dev write = 0
<369.057731> main: alsa xrun: try to recover...
<369.072061> main: alsa xrun: recovered.
<369.072078> main: dev write = 0
<369.092190> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<369.092215> DET_SYNC is received in RX_DPSK,rx->gain=0xa95
<369.119063> main: alsa xrun: try to recover...
<369.132064> main: alsa xrun: recovered.
<369.132080> main: dev write = 0
<369.132108> main: alsa xrun: try to recover...
<369.148061> main: alsa xrun: recovered.
<369.148076> main: dev read = 0
<369.161688> main: alsa xrun: try to recover...
<369.176071> main: alsa xrun: recovered.
<369.176093> main: dev write = 0
<369.176130> main: alsa xrun: try to recover...
<369.192061> main: alsa xrun: recovered.
<369.192078> main: dev read = 0
<369.218779> V34INFO, info0 CRC not received properly in DET_INFO
<369.218797> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
...
<369.724097> main: alsa xrun: try to recover...
<369.740063> main: alsa xrun: recovered.
<369.740084> main: dev read = 0
<369.760335> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<369.760360> DET_SYNC is received in RX_DPSK,rx->gain=0xbde
<369.760473> main: alsa xrun: try to recover...
<369.777065> main: alsa xrun: recovered.
<369.777086> main: dev write = 0
...
<369.855096> main: alsa xrun: try to recover...
<369.868049> main: alsa xrun: recovered.
<369.868065> main: dev write = 0
<369.881458> V34INFO, info0 CRC not received properly in DET_INFO
<369.881476> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<369.881680> main: alsa xrun: try to recover...
<369.896042> main: alsa xrun: recovered.
<369.896112> main: dev write = 0
...
<370.096186> main: alsa xrun: try to recover...
<370.112065> main: alsa xrun: recovered.
<370.112086> main: dev read = 0
<370.125632> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<370.125653> DET_SYNC is received in RX_DPSK,rx->gain=0xbde
<370.125760> main: alsa xrun: try to recover...
...
<370.241154> main: alsa xrun: try to recover...
<370.257068> main: alsa xrun: recovered.
<370.257085> main: dev read = 0
<370.277215> V34INFO, info0 CRC not received properly in DET_INFO
<370.277237> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<370.277425> main: alsa xrun: try to recover...
<370.292065> main: alsa xrun: recovered.
<370.292087> main: dev write = 0
<370.319050> main: alsa xrun: try to recover...
<370.332041> main: alsa xrun: recovered.
...
<370.404087> main: alsa xrun: recovered.
<370.404105> main: dev write = 0
<370.424361> main: alsa xrun: try to recover...
<370.441060> main: alsa xrun: recovered.
<370.441077> main: dev write = 0
<370.454344> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<370.454365> DET_SYNC is received in RX_DPSK,rx->gain=0xbdd
<370.454715> main: alsa xrun: try to recover...
<370.468059> main: alsa xrun: recovered.
<370.468074> main: dev write = 0
<370.481777> main: alsa xrun: try to recover...
<370.496064> main: alsa xrun: recovered.
<370.496085> main: dev write = 0
<370.509693> main: alsa xrun: try to recover...
<370.524063> main: alsa xrun: recovered.
<370.524083> main: dev write = 0
<370.544076> V34INFO, info0 CRC not received properly in DET_INFO
<370.544093> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<370.584380> main: alsa xrun: try to recover...
<370.600048> main: alsa xrun: recovered.
...
<370.764062> main: dev read = 0
<370.764069> main: alsa xrun: try to recover...
<370.780060> main: alsa xrun: recovered.
<370.780077> main: dev read = 0
<370.800398> main: alsa xrun: try to recover...
<370.816042> main: alsa xrun: recovered.
<370.816064> main: dev write = 0
<370.842928> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<370.842949> DET_SYNC is received in RX_DPSK,rx->gain=0xbd8
<370.843044> main: alsa xrun: try to recover...
<370.857056> main: alsa xrun: recovered.
<370.857073> main: dev write = 0
<370.870710> main: alsa xrun: try to recover...
<370.884062> main: alsa xrun: recovered.
...
<370.972167> main: alsa xrun: try to recover...
<370.988075> main: alsa xrun: recovered.
<370.988090> main: dev read = 0
<371.008277> V34INFO, info0 CRC not received properly in DET_INFO
<371.008302> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<371.008479> main: alsa xrun: try to recover...
<371.021069> main: alsa xrun: recovered.
<371.021086> main: dev write = 0
<371.034770> main: alsa xrun: try to recover...
<371.048042> main: alsa xrun: recovered.
<371.048064> main: dev write = 0
<371.075104> main: alsa xrun: try to recover...
<371.088053> main: alsa xrun: recovered.
...
<371.220079> main: dev read = 0
<371.220097> main: alsa xrun: try to recover...
<371.236078> main: alsa xrun: recovered.
<371.236104> main: dev read = 0
<371.262969> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<371.262991> DET_SYNC is received in RX_DPSK,rx->gain=0xbd7
<371.263143> main: alsa xrun: try to recover...
<371.276060> main: alsa xrun: recovered.
<371.276077> main: dev write = 0
...
<371.381432> main: alsa xrun: try to recover...
<371.396050> main: alsa xrun: recovered.
<371.396066> main: dev write = 0
<371.409592> V34INFO, info0 CRC not received properly in DET_INFO
<371.409609> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<371.409703> main: alsa xrun: try to recover...
<371.424043> main: alsa xrun: recovered.
<371.424058> main: dev write = 0
...
<371.512059> main: dev write = 0
<371.512081> main: alsa xrun: try to recover...
<371.528045> main: alsa xrun: recovered.
<371.528061> main: dev read = 0
<371.541521> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<371.541542> DET_SYNC is received in RX_DPSK,rx->gain=0xbd6
<371.561744> main: alsa xrun: try to recover...
...
<371.625061> main: alsa xrun: recovered.
<371.625078> main: dev write = 0
<371.625101> main: alsa xrun: try to recover...
<371.641061> main: alsa xrun: recovered.
<371.641085> main: dev read = 0
<371.654732> V34INFO, info0 CRC not received properly in DET_INFO
<371.654752> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<371.654805> main: alsa xrun: try to recover...
<371.668038> main: alsa xrun: recovered.
<371.668050> main: dev write = 0
...
<372.012090> main: dev write = 0
<372.012109> main: alsa xrun: try to recover...
<372.028052> main: alsa xrun: recovered.
<372.028069> main: dev read = 0
<372.048172> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<372.048194> DET_SYNC is received in RX_DPSK,rx->gain=0xbd4
<372.048446> main: alsa xrun: try to recover...
<372.064054> main: alsa xrun: recovered.
<372.064071> main: dev write = 0
<372.077675> main: alsa xrun: try to recover...
<372.092039> main: alsa xrun: recovered.
<372.092086> main: dev write = 0
...
<372.136079> main: dev write = 0
<372.149758> main: alsa xrun: try to recover...
<372.164062> main: alsa xrun: recovered.
<372.164080> main: dev write = 0
<372.177498> V34INFO, info0 CRC not received properly in DET_INFO
<372.177519> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<372.177737> main: alsa xrun: try to recover...
<372.192062> main: alsa xrun: recovered.
<372.192083> main: dev write = 0
<372.205715> main: alsa xrun: try to recover...
<372.220063> main: alsa xrun: recovered.
<372.220083> main: dev write = 0
...
<372.404060> main: dev write = 0
<372.430816> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<372.430836> DET_SYNC is received in RX_DPSK,rx->gain=0xbd3
<372.431025> main: alsa xrun: try to recover...
<372.444039> main: alsa xrun: recovered.
<372.444061> main: dev write = 0
<372.464359> main: alsa xrun: try to recover...
<372.480064> main: alsa xrun: recovered.
<372.480086> main: dev write = 0
<372.493712> main: alsa xrun: try to recover...
<372.508045> main: alsa xrun: recovered.
<372.508060> main: dev write = 0
<372.528247> V34INFO, info0 CRC not received properly in DET_INFO
<372.528266> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<372.528441> main: alsa xrun: try to recover...
<372.544061> main: alsa xrun: recovered.
<372.544077> main: dev write = 0
<372.577690> main: alsa xrun: try to recover...
<372.593081> main: alsa xrun: recovered.
<372.593108> main: dev write = 0
<372.606754> main: alsa xrun: try to recover...
<372.620060> main: alsa xrun: recovered.
<372.620076> main: dev write = 0
<372.673710> main: alsa xrun: try to recover...
<372.688050> main: alsa xrun: recovered.
<372.688066> main: dev write = 0
<372.694766> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<372.694790> DET_SYNC is received in RX_DPSK,rx->gain=0xbd2
<372.708397> main: alsa xrun: try to recover...
<372.724047> main: alsa xrun: recovered.
<372.724053> main: dev write = 0
<372.724061> main: alsa xrun: try to recover...
...
<372.840075> main: dev read = 0
<372.866796> V34INFO, info0 CRC not received properly in DET_INFO
<372.866815> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<372.867083> main: alsa xrun: try to recover...
<372.880037> main: alsa xrun: recovered.
...
<373.144060> main: dev read = 0
<373.184076> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<373.184098> DET_SYNC is received in RX_DPSK,rx->gain=0xbd2
<373.184413> main: alsa xrun: try to recover...
<373.200082> main: alsa xrun: recovered.
<373.200111> main: dev write = 0
...
<373.346708> V34INFO, info0 CRC not received properly in DET_INFO
<373.346725> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<373.367036> main: alsa xrun: try to recover...
<373.380050> main: alsa xrun: recovered.
<373.380072> main: dev write = 0
<373.393701> main: alsa xrun: try to recover...
<373.408061> main: alsa xrun: recovered.
<373.408076> main: dev write = 0
<373.408101> main: alsa xrun: try to recover...
<373.424060> main: alsa xrun: recovered.
<373.424081> main: dev read = 0
...
<380.088059> main: dev write = 0
<380.114920> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<380.114942> DET_SYNC is received in RX_DPSK,rx->gain=0xbc2
<380.115125> main: alsa xrun: try to recover...
<380.128046> main: alsa xrun: recovered.
<380.128062> main: dev write = 0
<380.148415> main: alsa xrun: try to recover...
...
<380.869097> main: dev write = 0
<380.882599> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<380.882622> DET_SYNC is received in RX_DPSK,rx->gain=0xbc0
<380.882845> main: alsa xrun: try to recover...
<380.896066> main: alsa xrun: recovered.
<380.896089> main: dev write = 0
...
<381.004088> main: dev write = 0
<381.017417> V34INFO, info0 CRC not received properly in DET_INFO
<381.017438> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<381.017739> main: alsa xrun: try to recover...
<381.032051> main: alsa xrun: recovered.
<381.032067> main: dev write = 0
<381.052364> main: alsa xrun: try to recover...
<381.068256> main: alsa xrun: recovered.
<381.068274> main: dev write = 0
...
<381.404044> main: alsa xrun: recovered.
<381.404060> main: dev write = 0
<381.444287> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<381.444309> DET_SYNC is received in RX_DPSK,rx->gain=0xbc0
<381.444401> main: alsa xrun: try to recover...
<381.460064> main: alsa xrun: recovered.
<381.460085> main: dev write = 0
...
<381.536045> main: alsa xrun: recovered.
<381.536061> main: dev write = 0
<381.549600> V34INFO, info0 CRC not received properly in DET_INFO
<381.549619> V34HSHAKE: microstate DET_INFO=>DET_SYNC(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<381.549795> main: alsa xrun: try to recover...
<381.564089> main: alsa xrun: recovered.
<381.564104> main: dev write = 0
...
<381.637061> main: alsa xrun: recovered.
<381.637078> main: dev read = 0
<381.643819> V34HSHAKE: microstate DET_SYNC=>DET_INFO(tx TX_DPSK, rx RX_DPSK, [1]0, [2]33)
<381.643840> DET_SYNC is received in RX_DPSK,rx->gain=0xbc0
<381.663813> main: alsa xrun: try to recover...
<381.676048> main: alsa xrun: recovered.
<381.676057> main: dev write = 0
<381.676065> main: alsa xrun: try to recover...
<381.692042> main: alsa xrun: recovered.
<381.692058> main: dev read = 0
<381.692066> main: alsa xrun: try to recover...
<381.708046> main: alsa xrun: recovered.
...
<381.740062> main: alsa xrun: recovered.
<381.740078> main: dev read = 0
<381.753478> vpcm: train timeout!
<381.753499> vpcm: Link Error
<381.753511> hw:0,6: modem_update_status: 4
<381.753522> hw:0,6: --> FINISH.
<381.753533> hw:0,6: modem_hup...
<381.753543> hw:0,6: modem set state: 2 --> 9...
<381.753554> hw:0,6: new state: DP_DISC
<381.753680> vpcm: train timeout!
<381.753768> vpcm: train timeout!
<381.753780> hw:0,6: modem_stop..
<381.753790> main: alsa_stop...
<381.768930> hw:0,6: modem set hook: 1 --> 0...
<381.768951> main: alsa_ioctl: cmd 2, arg 0...
<381.769074> main: alsa_ioctl: cmd 8, arg 0...
<381.769091> vpcm: delete...
<381.769175> $!$ ...
<381.769187> V90Phase3Demodulator: clearVerificationStatus called
<381.769201> V92EchoCanceller Destruction
<381.769214> V92Modem Destruction
<381.769244> V90Modem Destruction
<381.769325> $!$ ...
<381.769336> V90Phase3Demodulator: clearVerificationStatus called
<381.769433> hw:0,6: modem set state: 9 --> 1...
<381.769448> hw:0,6: new state: MODEM_IDLE
<381.769459> hw:0,6: modem report result: 3 (NO CARRIER)
<381.769483> main: dev write = 0
<381.969544> main: termios changed.
<381.969576> hw:0,6: update termios...
<381.969598> main: pty closed.
<391.134710> main: signal 2: mark termination.
<391.134867> hw:0,6: modem_delete...

```

It seems that something is happening. Infact, unplugging the modem cord I only get:
```

<424.017586> SmartLink Soft Modem: version 2.9.11 Dec 16 2008 22:54:51
<424.017680> hw:0,6: startup modem...
<424.017807> hw:0,6: update termios...
symbolic link `/dev/ttySL0' -> `/dev/pts/3' created.
modem `hw:0,6' created. TTY is `/dev/pts/3'
<424.018723> open file: /var/lib/slmodem/data.hw:0,6...
<424.021201> main: rt applyed: SCHED_FIFO, pri 99
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
<429.590539> main: termios changed.
<429.590589> hw:0,6: update termios...
<429.651038> main: termios changed.
<429.651067> hw:0,6: update termios...
<429.748155> hw:0,6: run cmd: ATZ
<429.748180> hw:0,6: modem reset...
<429.748191> hw:0,6: modem set state: 1 --> 1...
<429.748205> hw:0,6: modem set mode: -> 0...
<429.748216> hw:0,6: modem report result: 0 (OK)
<429.849441> hw:0,6: run cmd: ATQ0X3V1E1S0=0&C1&D2+FCLASS=0+MS=34
<429.849474> hw:0,6: modem set mode: -> 0...
<429.849488> hw:0,6: modem report result: 0 (OK)
<429.948455> hw:0,6: run cmd: ATDT7027020000
<429.948488> hw:0,6: modem dial: T7027020000...
<429.948500> hw:0,6: modem_dial_start...
<429.948512> call: create...
<429.948527> CallProgFP_Create >>
<429.948537> APPLY_FILTER = 0
<429.948550> Detection Thresholds: levle_fix=40,--> LEVEL_THRESHOLD=102
<429.948562> ============> 0
<429.948572> Cadence: Busy Tone loose detection is 0
<429.948585> TYPE BUSY
<429.948595> Filter index 0
<429.948605> Filter SubIndex 0
<429.948615> MAX_ON_TIME 27 Buffers     MIN_ON_TIME 10 Buffers
<429.948626> MAX_OFF_TIME 27 Buffers    MIN_OFF_TIME 10 Buffers
<429.948636> OFF_TIME_THAT_RESETS_CYCLE 81
<429.948646> BUFFER LENGTH 160 samples.
<429.948656> INTEGRATION_LENGTH 0[ms]
<429.948667> LEVEL 102
<429.948680> INTEGRATION_TIME = 0 Buffers.
<429.948692> Detection Thresholds: levle_fix=40,--> LEVEL_THRESHOLD=102
<429.948704> TYPE DIAL
<429.948714> Filter index 4
<429.948724> Filter SubIndex 0
<429.948734> MAX_ON_TIME 0 Buffers     MIN_ON_TIME 0 Buffers
<429.948744> MAX_OFF_TIME 0 Buffers    MIN_OFF_TIME 0 Buffers
<429.948755> OFF_TIME_THAT_RESETS_CYCLE 0
<429.948765> BUFFER LENGTH 666 samples.
<429.948774> INTEGRATION_LENGTH 1500[ms]
<429.948785> LEVEL 102
<429.948796> INTEGRATION_TIME = 16 Buffers.
<429.948809> CALLPROG Create <<
<429.948819> CALLPROG Dialing T7027020000
<429.948831> Configuration->tone_DigitLength 100
<429.948841> Configuration->pulse_OffHookTime 41
<429.948851> Configuration->pulse_OnHookTime 65
<429.948861> Configuration->dialPauseTime 2
<429.948872> Configuration->flashTime 11
<429.948882> Configuration->toneOrPulseFlag 0
<429.948892> Configuration->dialModifierValidationFlag 1
<429.948903> Configuration->ABCD_PermittedFlag 0
<429.948913> Configuration->pulseAndToneInSameStringPermittedFlag 0
<429.948924> Configuration->callingToneFlag 0
<429.948934> Configuration->commaPauseDurLimit 30
<429.948944> Configuration->digitPattern 1
<429.948954> Configuration->tone_BetweenDigitsInterval 100
<429.948965> Configuration->pulse_BetweenDigitsInterval 800
<429.948975> DTMF_Gain1 = 10337
<429.948985> DTMF_Gain2 = 13014
<429.948997> AnalyzeDialString: Updated 17 May 1999 00:50
<429.949007> AnalyzeDialString: LAST_DIALABLE_SYMBOL is 10
<429.949017> Dial String Syntax is VALID
<429.949031> GetNoAnswerTimeOut. 60
<429.949042> BlindCall: GetBlindDialPause = 2 .
<429.949052> CALLPROG_Dial was exited.
<429.949062> call: create RC: 9600 <-> 8000...
<429.949076> hw:0,6: modem_start..
<429.949086> hw:0,6: modem set state: 1 --> 2...
<429.949098> hw:0,6: new state: DP_ESTAB
<429.949108> main: alsa_ioctl: cmd 8, arg 3...
<429.949119> hw:0,6: modem set hook: 0 --> 1...
<429.949130> main: alsa_ioctl: cmd 2, arg 1...
<429.949251> main: alsa_ioctl: cmd 11, arg 0...
<429.949328> main: alsa_ioctl: cmd 4, arg 2580...
<429.949342> main: alsa_ioctl: cmd 7, arg 30...
<429.949353> main: alsa_start...
Hardware PCM card 0 'HDA Intel' device 6 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 9600
  exact rate   : 9600 (9600/1)
  msbits       : 16
  buffer_size  : 2048
  period_size  : 64
  period_time  : 6666
  tick_time    : 0
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 64
  xfer_align   : 4
  start_threshold  : 2147483647
  stop_threshold   : 2048
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Hardware PCM card 0 'HDA Intel' device 6 subdevice 0
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 9600
  exact rate   : 9600 (9600/1)
  msbits       : 16
  buffer_size  : 2048
  period_size  : 64
  period_time  : 6666
  tick_time    : 0
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 64
  xfer_align   : 4
  start_threshold  : 2147483647
  stop_threshold   : 2048
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
<429.980298> main: startup write: 384...
<429.993693> call: process: msg 18 --> 0
<431.586968> DCR: initial DC Evaluation done, DC level -32768, enabled
<431.993642> CALLPROG: Time out
<431.993676> STATE:  CALLPROG_WAIT_DIAL --> CALLPROG_DIALING
<431.993698> call: process: msg 0 --> 3
<431.993719> DIALER_INITIAL_STATE
<431.993730> Digit is T
<431.993741> Dialer.c: GetNextDigit... TONE_OR_PULSE_FLAG became TONE_DIALING
<431.993752> Digit is 7
<431.993762> Samples left = 800
<431.993787> call: process: msg 3 --> 0
<432.093645> Done Generating digit
<432.186983> Done Generating silence between digits
<432.187002> Digit is 0
<432.187012> Samples left = 800
...
<433.886972> Done Generating digit
<433.893630> DIALER_END_STATE
<433.893647> STATE:  CALLPROG_DIALING --> CALLPROG_WAIT_RING
<433.893668> call: process: msg 0 --> 4
<433.906974> call: process: msg 4 --> 0
<489.084381> hw:0,6: modem_tty_write: hangup...
<489.084430> hw:0,6: modem_hup...
<489.084444> hw:0,6: modem set state: 2 --> 9...
<489.084457> hw:0,6: new state: DP_DISC
<489.084476> main: termios changed.
<489.084487> hw:0,6: update termios...
<489.084507> main: pty closed.
<489.093053> hw:0,6: modem_stop..
<489.093081> main: alsa_stop...
<489.112048> hw:0,6: modem set hook: 1 --> 0...
<489.112075> main: alsa_ioctl: cmd 2, arg 0...
<489.112191> main: alsa_ioctl: cmd 8, arg 0...
<489.112207> call: delete...
<489.112218> Dialer was aborted.
<489.112234> CALLPROG_Delete is entered
<489.112244> cadence_delete with CADENCE_DIAL_OBJ is invoked
<489.112255> cadence_delete with CADENCE_OBJ is invoked
<489.112266> CALLPROG_Delete is exited
<489.112278> hw:0,6: modem set state: 9 --> 1...
<489.112290> hw:0,6: new state: MODEM_IDLE
<489.112301> hw:0,6: modem report result: 3 (NO CARRIER)
<489.112321> main: dev write = 0
<515.074031> main: signal 2: mark termination.
<515.074139> hw:0,6: modem_delete...

```

What sounds strange to me is the long sequence of:
```

<381.676065> main: alsa xrun: try to recover...
<381.692042> main: alsa xrun: recovered.

```
ended by a:
```

<381.753478> vpcm: train timeout!
<381.753499> vpcm: Link Error

```
I'd like to know at least if I managed to call the modem on the other end of the line (I don't hear any modem talking with mine in their funny language, but that could be just a matter of sound settings). But there's a V34HSHAKE which I am tempted to read as "Hi, nice to meet you".

For comparison I post the log of the modem in windows:
```

115200,8,N,1, ctsfl=1, rtsctl=2
Inizializzazione modem in corso.
Invio: 	AT<cr>
Ricezione:	<cr><lf>OK<cr><lf>
risposta interpretata: OK
Invio: 	AT&F&D2&C1V1S0=0E0<cr>
Ricezione:	<cr><lf>OK<cr><lf>
risposta interpretata: OK
Invio: 	ATS7=60\T0L0M1\N7%C1\Q3*LS1X4<cr>
Ricezione:	<cr><lf>OK<cr><lf>
risposta interpretata: OK
Composizione del numero in corso.
Invio: 	ATDT##########<cr>
Ricezione:	<cr><lf>CONNECT 52000/LAPM<cr><lf>
risposta interpretata: Connetti
Connessione stabilita a 52000bps.

```
I am trying to reproduce the win initialization sequence (with the help of some "AT Commands and S-Registers Reference Guide" found on the web), but no all the commands are accepted.

---

### Post by _duncan_ on 2008-12-26
I'm not convinced the init string is causing the problem. I've worked with maybe 5 or 6 winmodems before and the default init string supplied by wvdial is often enough. The one time I had to change it was when I tried a really old U.S. Robotics serial hardware modem. Even with a faulty init string, the modem can still communicate with the ISP but just can't authenticate.

If you're game, there are a couple of things we can try:

1. Use a different dialer program. For some strange reason I can never get wvdial to work with a SL2800 smartlink chipset, while _pppconfig_ works flawlessly. You don't have to install additional packages since pppconfig comes with a default Ubuntu install. If you want to try type this in a terminal:

```
sudo pppconfig
```

An interface similar to a DOS-based windows program will appear. Just follow the instructions to set up your connection data. Leave the default name as 'provider'.

After saving the configuration, type

```
pon
``` to try to connect.

There are 2 other terminal commands to know: _poff_ will disconnect, while _plog_ will list details of the last connection attempt.


2. Try compiling the open-source driver (slmodem-2.9.11-20080817.tar.gz). I noticed in your earlier post you were unable to compile successfully. Have you installed the 'build-essential' package before compiling? If not, that would explain the compilation error. Post back if you need help installing the package.

--------------

Your /etc/resolv.conf file looks odd. For dial-up, I expect 2 lines representing the primary and secondary DNS servers. Thus it should look like:

```
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
```

Also, the address 10.0.0.1 looks like the kind of address you get when connected via LAN or router. I'm not an authority on these though, so I can be wrong.

Let's leave this discussion about /etc/resolv.conf for now and focus on the above 2 options. From what I recall, the dialer program may overwrite this file anyway if you are successful connecting to your ISP.

---

### Post by imbuto on 2008-12-28
Hi,

1. I tried using pppconfig as you suggested, but with the same result.
If I set just the general options (ISP information) it simply won't dial with the modem daemon reporting "No Dialtone".
Again, I have to play with the initialization strings in the advanced settings to get it dial. With a modem initialization string changed from "ATZ" (modem defaults) to "ATQ0 X3" (the first part of Init2 I had in wvdial), I get the same output I posted in the last message. So apparently it makes no difference.

2. 'build-essential' is not installed (I thought it was)... but now I don't have neither the ubuntu CD handy - I forgot it some hundreds km away - nor internet access from linux, of course. I'll try to download 'manually' the deb package from the official repository under windows and install it in the next days... but I fear that won't solve the problem.

-----
My /etc/resolv.conf probably looks like this because I used to connect to a Wireless network and, you're right, the dialer program will anyway overwrite the file once you connect, if you choose to retrieve names dynamically in pppconfig.

---

### Post by _duncan_ on 2008-12-28
I went through the same process with the modem logs in Windows XP to get a US Robotics modem working in Ubuntu about 3 years ago. From what I can discern from the logs your wvdial should contain the following init strings:

```
Init1 = ATZ
Init2 = AT&F&D2&C1V1S0=0E0
Init3 = ATS7=60\T0L0M1\N7%C1\Q3*LS1X4
```

Is this what you tried before?

----------

Have to warn you that I don't know what these codes mean. From what I can recall, I merely copy/paste the strings from modemlogs from XP to the ubuntu dialer settings and the modem worked. Mine had more than 3 lines.

----------

There used to be a website that lists the init strings of modems. I can't find the site anymore, but I kept a local copy. It is a very long list, but I'll reproduce the portion dealing with Intel

```
96/96 for PCMCIA	ATS0=0 E1Q0V1X4&K3^M
International-Faxmodem 96/96 for PCMCIA(EEC)	ATS0=0 E1Q0V1X4&K3^M
SatisFAXtion Modem/400e	ATS0=0 E1Q0V1X4 &C1&D2&M0\G0\K5^M AT \Q3%C0\V3L0^M
SatisFAXtion Modem/400	ATS0=0 E1Q0V1X4 &C1&D2&M0&Q0\G0\K5^M AT \Q3%C0\V3L0^M
SatisFAXtion Modem/350	ATS0=0 E1Q0V1X4 &C1&D2&M0&Q0\G0\K5^M AT \Q3%C0\V3L0^M
SatisFAXtion Modem/300	ATS0=0 E1Q0V1X4 &C1&D2&M0&Q0\G0\K5^M AT \Q3%C0\V3L0^M
SatisFAXtion Classic	ATS0=0 E1Q0V1X4 &C1&D2&M0&Q0\G0\K5^M AT \Q3%C0\V3L0^M
PCMCIA 96/96	ATS0=0 E1Q0V1X4&K3^M
PCMCIA 14.4/14.4	ATS0=0 E1Q0V1X4&K3^M
Other	ATS0=0 E1Q0V1X4^M
International-Faxmodem 96/96 for PCMCIA(FRA)	ATS0=0 E1Q0V1X4&K3^M
International-Faxmodem 14.4/14.4 for PCMCIA	ATS0=0 E1Q0V1X4&K3^M
Faxmodem 14.4/14.4 for PCMCIA(MBFM6831)	ATS0=0 E1Q0V1X4 &C1&D2&Q0\N0^M
Faxmodem 14.4/14.4 for PCMCIA(MBFM6830)	ATS0=0 E1Q0V1X4 &C1&D2&Q0\N0^M
9600EX	ATV1Q0X4&C1&D2\N3\J0\Q3\V1%C0^M
96/96 for PCMCIA(MBFM6820)	ATS0=0 E1Q0V1X4&K3^M
96/96	ATS0=0 E1Q0V1X4 &C1&D2&Q0\N0\Q3^M
144/144i	ATS0=0 E1Q0V1X4 &C1&D2&Q0\N0\Q3^M
144/144e	ATS0=0 E1Q0V1X4 &C1&D2&Q0\N0\Q3^M
14.4EX with v.32BIS	ATV1Q0X4&C1&D2\N3\J0\Q3\V1%C0^M
96/96 for PCMCIA(MBFM6821)	ATS0=0 E1Q0V1X4&K3^M
```

Not sure if they are useful, but since you're researching AT commands, it may give you some hints.

---

### Post by imbuto on 2009-01-09
I decided to give up, temporarily at least. I found several discussion on the web reporting tha same behavior, but none of them seems to have had a happy end.
Disappointing and frustrating.

---

### Post by sir_cheats_a_lot on 2012-04-29
did you ever get anywhere with this?   I've the exact same modem, more or less the same problem.  I think it is more of a wvdial issue, though I don't know for certain.  for whatever reason, however, it seems to be ignoring the carrier check/stupid mode options altogether.  except, mine will actually connect once or twice every hundred or so tries.   but those connections are quite unstable. Different version of Ubuntu however, I'm using 12.04(I should really be making a new thread).  most attempts are met with a no carrier error, followed, by either a never ending loop of them, or simply it'll claim there's no dial tone.

---

