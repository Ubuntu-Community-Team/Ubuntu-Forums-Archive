---
title: "Mgetty with  ESS modem"
date: 2009-12-10
forum: Hardware
---

### Post by HectorG on 2009-12-10
I am trying to use MGETTY as a caller ID and eventually build in the function to use a mysql db and block calls on a list. 

I am having a problem when I reboot the machine and someone calls it locks up my machine and the only way to get it back is to reboot.

I have narrowed it down but I am still nopt sure what is causing it.

It works correctly when I do the following
1. restart machine
2. stop mgetty
3. comment out port config from mgetty.config this includes the init chat and cmd line
4 start mgetty
5. call number and hag up after 2nd ring
6 stop mgety
7. uncomment port config from mgetty.config this includes the init chat and cmd line
8. start mgetty
At this point if someone calls my caller id does work

If I dont do it as shown above like I said before on the second ring it hangs up everything...

Anyway here is my config...

/etc/mgetty/mgetty.config
```

debug 8 # Log everything to /var/log/mgetty/mg_ttyS_ESS0.log
speed 115200 # Buad rate to run modem at
rings 2 # Answer phone after 2 rings - Need 2 because caller id info is sent between 1st and 2nd ring
# The following tells mgetty that for ttyS_ESS0 turn caller id on and run callerid.sh
issue-file /etc/issue.mgetty
port ttyS_ESS0
  init-chat "" AT#CID=1 OK
  cnd-program /home/ubuntuuser/scripts/callerid/callerid.sh

```
callerid.sh

```

#!/bin/sh
NUMBER="$2"
NAME="$3"

echo "Incoming call from $NAME. $NUMBER" | festival --tts

exit 1 # So mgetty will NOT answer the phone!

```

/etc/init/mgetty.conf


```

start on startup

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

respawn
exec /sbin/mgetty /dev/ttyS_ESS0

``````

ubuntuuser@ubuntu:/etc/mgetty$ sudo wvdialconf  wvtest
Editing `wvtest'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttyS_ESS0 first, /dev/modem is a link to it.
ttyS_ESS0<*1>: ATQ0 V1 E1 -- OK
ttyS_ESS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS_ESS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS_ESS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS_ESS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS_ESS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS_ESS0<*1>: Modem Identifier: ATI -- 56000/33600
ttyS_ESS0<*1>: Speed 4800: AT -- OK
ttyS_ESS0<*1>: Speed 9600: AT -- OK
ttyS_ESS0<*1>: Speed 19200: AT -- OK
ttyS_ESS0<*1>: Speed 38400: AT -- OK
ttyS_ESS0<*1>: Speed 57600: AT -- OK
ttyS_ESS0<*1>: Speed 115200: AT -- OK
ttyS_ESS0<*1>: Max speed is 115200; that should be safe.
ttyS_ESS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 -- &#65533;[01]A?Z&#65533;h&#65533;&#65533;=Q&#65533;[07]V&#65533;&#65533;[7f][0f]F&#65533;?'&#65533;&#65533;j[17]&#65533;&#65533;~&#65533;[0f][16]&#65533;/[17]o[01][&#65533;&#65533;b&#65533;7f]&#65533;[03][&#65533;Eo[0f][16]={+&#65533;&#65533;r&#65533;)"8[0e]&#65533;[[0f][17][07][0b]&#65533;[1f]&#65533;[1f]_i&#65533;NNNNNtNNNNNNvNNNND"[16]-&#65533;[0f][15]&#65533;&#65533;&&#65533;j&#65533;
ttyS0<*1>: failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- Password:
ttyS0<*1>: failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   

Found a modem on /dev/ttyS_ESS0, using link /dev/modem in config.
wvtest<Warn>: Can't open 'wvtest' for reading: No such file or directory
wvtest<Warn>: ...starting with blank configuration.
Modem configuration written to wvtest.
ttyS_ESS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ubuntuuser@ubuntu:/etc/mgetty$ 
```
I appreciate any help...

---

### Post by HectorG on 2009-12-19
I tried vgetty also now and still nothing. Actuall with vgetty it is worst after the first ring it locks up my pc. Is there anything special that has to be done for ESS modems?


here is my log with debug set to 8 (it locks up after it rings once.


```

--
12/19 23:11:00 SS0  vgetty: experimental test release 0.9.32 / with duplex patch
12/19 23:11:00 SS0  mgetty: interim release 1.1.36-Jun15
12/19 23:11:00 SS0  reading generic configuration from config file /etc/mgetty/voice.conf
12/19 23:11:00 SS0  reading program vgetty configuration from config file /etc/mgetty/voice.conf
12/19 23:11:00 SS0   reading /etc/mgetty/voice.conf...
12/19 23:11:00 SS0   conf lib: read: 'voice_log_level 8'
12/19 23:11:00 SS0   conf lib: read: 'voice_shell_log /var/log/vgetty_voice_shell.%s'
12/19 23:11:00 SS0   conf lib: read: 'voice_dir /var/spool/voice'
12/19 23:11:00 SS0   conf lib: read: 'phone_owner root'
12/19 23:11:00 SS0   conf lib: read: 'phone_group voice'
12/19 23:11:00 SS0   conf lib: read: 'phone_mode 0660'
12/19 23:11:00 SS0   conf lib: read: 'message_flag_file .flag'
12/19 23:11:00 SS0   conf lib: read: 'receive_dir incoming'
12/19 23:11:00 SS0   conf lib: read: 'message_dir messages'
12/19 23:11:00 SS0   conf lib: read: 'message_list Index'
12/19 23:11:00 SS0   conf lib: read: 'backup_message standard.rmd'
12/19 23:11:00 SS0   conf lib: read: 'port_speed 115200'
12/19 23:11:00 SS0   conf lib: read: 'voice_shell /bin/sh'
12/19 23:11:00 SS0   conf lib: read: 'port_timeout 10'
12/19 23:11:00 SS0   conf lib: read: 'dial_timeout 90'
12/19 23:11:00 SS0   conf lib: read: 'command_delay 100'
12/19 23:11:00 SS0   conf lib: read: 'dtmf_len 30'
12/19 23:11:00 SS0   conf lib: read: 'dtmf_threshold 40'
12/19 23:11:00 SS0   conf lib: read: 'dtmf_wait 7'
12/19 23:11:00 SS0   conf lib: read: 'ignore_fax_dle false'
12/19 23:11:00 SS0   conf lib: read: 'raw_data false'
12/19 23:11:00 SS0   conf lib: read: 'rec_compression 0'
12/19 23:11:00 SS0   conf lib: read: 'rec_speed 0'
12/19 23:11:00 SS0   conf lib: read: 'rec_silence_len 70'
12/19 23:11:00 SS0   conf lib: read: 'rec_silence_threshold 40'
12/19 23:11:00 SS0   conf lib: read: 'rec_remove_silence false'
12/19 23:11:00 SS0   conf lib: read: 'rec_max_len 300'
12/19 23:11:00 SS0   conf lib: read: 'rec_min_len 0'
12/19 23:11:00 SS0   conf lib: read: 'do_hard_flow true'
12/19 23:11:00 SS0   conf lib: read: 'beep_frequency 933'
12/19 23:11:00 SS0   conf lib: read: 'beep_length 1500'
12/19 23:11:00 SS0   conf lib: read: 'max_tries 3'
12/19 23:11:00 SS0   conf lib: read: 'retry_delay 5'
12/19 23:11:00 SS0   conf lib: read: 'watchdog_timeout 60'
12/19 23:11:00 SS0   conf lib: read: 'receive_gain -1'
12/19 23:11:00 SS0   conf lib: read: 'transmit_gain -1'
12/19 23:11:00 SS0   conf lib: read: 'enable_command_echo false'
12/19 23:11:00 SS0   conf lib: read: 'poll_interval 10'
12/19 23:11:00 SS0   conf lib: read: 'forceV253 TRUE'
12/19 23:11:00 SS0   conf lib: read: 'enable_compression_mapping_querry TRUE'
12/19 23:11:00 SS0   conf lib: read: 'compression_8bit_linear_signed 0'
12/19 23:11:00 SS0   conf lib: read: 'compression_16bit_linear_signed 0'
12/19 23:11:00 SS0   conf lib: read: 'compression_8bit_linear_unsigned 1'
12/19 23:11:00 SS0   conf lib: read: 'compression_8bit_ulaw 4'
12/19 23:11:00 SS0   conf lib: read: 'compression_8bit_alaw 5'
12/19 23:11:00 SS0   conf lib: read: 'compression_2bit_adpcm 140'
12/19 23:11:00 SS0   conf lib: read: 'compression_4bit_adpcm 141'
12/19 23:11:00 SS0   conf lib: read: 'compression_4bit_ima_adpcm 129'
12/19 23:11:00 SS0   conf lib: read: 'program vgetty'
12/19 23:11:00 SS0   section: program vgetty, **found**
12/19 23:11:00 SS0   conf lib: read: 'rings 3'
12/19 23:11:00 SS0   conf lib: read: 'answer_mode voice:fax:data'
12/19 23:11:00 SS0   conf lib: read: 'force_autodetect false'
12/19 23:11:00 SS0   conf lib: read: 'toll_saver_rings 0'
12/19 23:11:00 SS0   conf lib: read: 'rec_always_keep true'
12/19 23:11:00 SS0   conf lib: read: 'call_program /home/user/say_callerid.sh'
12/19 23:11:00 SS0   conf lib: read: 'dtmf_program dtmf.sh'
12/19 23:11:00 SS0   conf lib: read: 'do_message_light false'
12/19 23:11:00 SS0   conf lib: read: 'ring_report_delay 15'
12/19 23:11:00 SS0   conf lib: read: 'program vm'
12/19 23:11:00 SS0   section: program vm, ignore
12/19 23:11:00 SS0   conf lib: read: 'voice_devices '
12/19 23:11:00 SS0   conf lib: read: 'dialout_timeout 90'
12/19 23:11:00 SS0   conf lib: read: 'ringback_goes_away 70'
12/19 23:11:00 SS0   conf lib: read: 'ringback_never_came 100'
12/19 23:11:00 SS0   conf lib: read: 'program pvf'
12/19 23:11:00 SS0   section: program pvf, ignore
12/19 23:11:00 SS0   conf lib: read: 'port ttyS_ESS0'
12/19 23:11:00 SS0   conf lib: read: 'ring_type ring'
12/19 23:11:00 SS0   key: 'part', type=6, flags=4, data=(ignored)
12/19 23:11:00 SS0   key: 'program', type=6, flags=4, data=(ignored)
12/19 23:11:00 SS0   key: 'port', type=6, flags=4, data=(ignored)
12/19 23:11:00 SS0   key: 'ring_type', type=6, flags=4, data=(ignored)
12/19 23:11:00 SS0   key: 'voice_log_level', type=0, flags=3, data=8
12/19 23:11:00 SS0   key: 'voice_shell_log', type=1, flags=3, data=/var/log/vgetty_voice_shell.%s
12/19 23:11:00 SS0   key: 'voice_shell', type=1, flags=3, data=/bin/sh
12/19 23:11:00 SS0   key: 'port_speed', type=0, flags=3, data=115200
12/19 23:11:00 SS0   key: 'port_timeout', type=0, flags=3, data=10
12/19 23:11:00 SS0   key: 'dial_timeout', type=0, flags=3, data=90
12/19 23:11:00 SS0   key: 'command_delay', type=0, flags=3, data=100
12/19 23:11:00 SS0   key: 'dtmf_len', type=0, flags=3, data=30
12/19 23:11:00 SS0   key: 'dtmf_threshold', type=0, flags=3, data=40
12/19 23:11:00 SS0   key: 'dtmf_wait', type=0, flags=3, data=7
12/19 23:11:00 SS0   key: 'ignore_fax_dle', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'raw_data', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'rec_compression', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'rec_speed', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'rec_silence_len', type=0, flags=3, data=70
12/19 23:11:00 SS0   key: 'rec_silence_threshold', type=0, flags=3, data=40
12/19 23:11:00 SS0   key: 'rec_remove_silence', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'rec_max_len', type=0, flags=3, data=300
12/19 23:11:00 SS0   key: 'rec_min_len', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'do_hard_flow', type=3, flags=3, data=TRUE
12/19 23:11:00 SS0   key: 'force_autodetect', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'watchdog_timeout', type=0, flags=3, data=60
12/19 23:11:00 SS0   key: 'receive_gain', type=0, flags=3, data=-1
12/19 23:11:00 SS0   key: 'transmit_gain', type=0, flags=3, data=-1
12/19 23:11:00 SS0   key: 'enable_command_echo', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'poll_interval', type=0, flags=3, data=10
12/19 23:11:00 SS0   key: 'forceV253', type=3, flags=3, data=TRUE
12/19 23:11:00 SS0   key: 'forceV253subset', type=3, flags=1, data=FALSE
12/19 23:11:00 SS0   key: 'enable_compression_mapping_querry', type=3, flags=3, data=TRUE
12/19 23:11:00 SS0   key: 'compression_8bit_linear_signed', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'compression_16bit_linear_signed', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'compression_8bit_linear_unsigned', type=0, flags=3, data=1
12/19 23:11:00 SS0   key: 'compression_8bit_ulaw', type=0, flags=3, data=4
12/19 23:11:00 SS0   key: 'compression_8bit_alaw', type=0, flags=3, data=5
12/19 23:11:00 SS0   key: 'compression_2bit_adpcm', type=0, flags=3, data=140
12/19 23:11:00 SS0   key: 'compression_4bit_adpcm', type=0, flags=3, data=141
12/19 23:11:00 SS0   key: 'compression_4bit_ima_adpcm', type=0, flags=3, data=129
12/19 23:11:00 SS0   key: 'rings', type=1, flags=3, data=3
12/19 23:11:00 SS0   key: 'answer_mode', type=1, flags=3, data=voice:fax:data
12/19 23:11:00 SS0   key: 'toll_saver_rings', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'rec_always_keep', type=3, flags=3, data=TRUE
12/19 23:11:00 SS0   key: 'voice_dir', type=1, flags=3, data=/var/spool/voice
12/19 23:11:00 SS0   key: 'phone_owner', type=1, flags=3, data=root
12/19 23:11:00 SS0   key: 'phone_group', type=1, flags=3, data=voice
12/19 23:11:00 SS0   key: 'phone_mode', type=0, flags=3, data=432
12/19 23:11:00 SS0   key: 'message_flag_file', type=1, flags=3, data=.flag
12/19 23:11:00 SS0   key: 'receive_dir', type=1, flags=3, data=incoming
12/19 23:11:00 SS0   key: 'message_dir', type=1, flags=3, data=messages
12/19 23:11:00 SS0   key: 'message_list', type=1, flags=3, data=Index
12/19 23:11:00 SS0   key: 'backup_message', type=1, flags=3, data=standard.rmd
12/19 23:11:00 SS0   key: 'button_program', type=1, flags=1, data=
12/19 23:11:00 SS0   key: 'call_program', type=1, flags=3, data=/home/hector/MyStuff/scripts/callerid/say_callerid.sh
12/19 23:11:00 SS0   key: 'dtmf_program', type=1, flags=3, data=dtmf.sh
12/19 23:11:00 SS0   key: 'message_program', type=1, flags=1, data=
12/19 23:11:00 SS0   key: 'do_message_light', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'pre_message', type=1, flags=1, data=
12/19 23:11:00 SS0   key: 'beepsound', type=1, flags=1, data=
12/19 23:11:00 SS0   key: 'beep_frequency', type=0, flags=3, data=933
12/19 23:11:00 SS0   key: 'beep_length', type=0, flags=3, data=1500
12/19 23:11:00 SS0   key: 'max_tries', type=0, flags=3, data=3
12/19 23:11:00 SS0   key: 'retry_delay', type=0, flags=3, data=5
12/19 23:11:00 SS0   key: 'dialout_timeout', type=0, flags=1, data=90
12/19 23:11:00 SS0   key: 'ringback_goes_away', type=0, flags=1, data=70
12/19 23:11:00 SS0   key: 'ringback_never_came', type=0, flags=1, data=100
12/19 23:11:00 SS0   key: 'ring_report_delay', type=0, flags=3, data=15
12/19 23:11:00 SS0   key: 'voice_devices', type=1, flags=1, data=
12/19 23:11:00 SS0  reading port ttyS_ESS0 configuration from config file /etc/mgetty/voice.conf
12/19 23:11:00 SS0   reading /etc/mgetty/voice.conf...
12/19 23:11:00 SS0   conf lib: read: 'voice_log_level 8'
12/19 23:11:00 SS0   conf lib: read: 'voice_shell_log /var/log/vgetty_voice_shell.%s'
12/19 23:11:00 SS0   conf lib: read: 'voice_dir /var/spool/voice'
12/19 23:11:00 SS0   conf lib: read: 'phone_owner root'
12/19 23:11:00 SS0   conf lib: read: 'phone_group voice'
12/19 23:11:00 SS0   conf lib: read: 'phone_mode 0660'
12/19 23:11:00 SS0   conf lib: read: 'message_flag_file .flag'
12/19 23:11:00 SS0   conf lib: read: 'receive_dir incoming'
12/19 23:11:00 SS0   conf lib: read: 'message_dir messages'
12/19 23:11:00 SS0   conf lib: read: 'message_list Index'
12/19 23:11:00 SS0   conf lib: read: 'backup_message standard.rmd'
12/19 23:11:00 SS0   conf lib: read: 'port_speed 115200'
12/19 23:11:00 SS0   conf lib: read: 'voice_shell /bin/sh'
12/19 23:11:00 SS0   conf lib: read: 'port_timeout 10'
12/19 23:11:00 SS0   conf lib: read: 'dial_timeout 90'
12/19 23:11:00 SS0   conf lib: read: 'command_delay 100'
12/19 23:11:00 SS0   conf lib: read: 'dtmf_len 30'
12/19 23:11:00 SS0   conf lib: read: 'dtmf_threshold 40'
12/19 23:11:00 SS0   conf lib: read: 'dtmf_wait 7'
12/19 23:11:00 SS0   conf lib: read: 'ignore_fax_dle false'
12/19 23:11:00 SS0   conf lib: read: 'raw_data false'
12/19 23:11:00 SS0   conf lib: read: 'rec_compression 0'
12/19 23:11:00 SS0   conf lib: read: 'rec_speed 0'
12/19 23:11:00 SS0   conf lib: read: 'rec_silence_len 70'
12/19 23:11:00 SS0   conf lib: read: 'rec_silence_threshold 40'
12/19 23:11:00 SS0   conf lib: read: 'rec_remove_silence false'
12/19 23:11:00 SS0   conf lib: read: 'rec_max_len 300'
12/19 23:11:00 SS0   conf lib: read: 'rec_min_len 0'
12/19 23:11:00 SS0   conf lib: read: 'do_hard_flow true'
12/19 23:11:00 SS0   conf lib: read: 'beep_frequency 933'
12/19 23:11:00 SS0   conf lib: read: 'beep_length 1500'
12/19 23:11:00 SS0   conf lib: read: 'max_tries 3'
12/19 23:11:00 SS0   conf lib: read: 'retry_delay 5'
12/19 23:11:00 SS0   conf lib: read: 'watchdog_timeout 60'
12/19 23:11:00 SS0   conf lib: read: 'receive_gain -1'
12/19 23:11:00 SS0   conf lib: read: 'transmit_gain -1'
12/19 23:11:00 SS0   conf lib: read: 'enable_command_echo false'
12/19 23:11:00 SS0   conf lib: read: 'poll_interval 10'
12/19 23:11:00 SS0   conf lib: read: 'forceV253 TRUE'
12/19 23:11:00 SS0   conf lib: read: 'enable_compression_mapping_querry TRUE'
12/19 23:11:00 SS0   conf lib: read: 'compression_8bit_linear_signed 0'
12/19 23:11:00 SS0   conf lib: read: 'compression_16bit_linear_signed 0'
12/19 23:11:00 SS0   conf lib: read: 'compression_8bit_linear_unsigned 1'
12/19 23:11:00 SS0   conf lib: read: 'compression_8bit_ulaw 4'
12/19 23:11:00 SS0   conf lib: read: 'compression_8bit_alaw 5'
12/19 23:11:00 SS0   conf lib: read: 'compression_2bit_adpcm 140'
12/19 23:11:00 SS0   conf lib: read: 'compression_4bit_adpcm 141'
12/19 23:11:00 SS0   conf lib: read: 'compression_4bit_ima_adpcm 129'
12/19 23:11:00 SS0   conf lib: read: 'program vgetty'
12/19 23:11:00 SS0   found CT_KEYWORD program vgetty
12/19 23:11:00 SS0   conf lib: read: 'rings 3'
12/19 23:11:00 SS0   conf lib: read: 'answer_mode voice:fax:data'
12/19 23:11:00 SS0   conf lib: read: 'force_autodetect false'
12/19 23:11:00 SS0   conf lib: read: 'toll_saver_rings 0'
12/19 23:11:00 SS0   conf lib: read: 'rec_always_keep true'
12/19 23:11:00 SS0   conf lib: read: 'call_program /home/user/say_callerid.sh'
12/19 23:11:00 SS0   conf lib: read: 'dtmf_program dtmf.sh'
12/19 23:11:00 SS0   conf lib: read: 'do_message_light false'
12/19 23:11:00 SS0   conf lib: read: 'ring_report_delay 15'
12/19 23:11:00 SS0   conf lib: read: 'program vm'
12/19 23:11:00 SS0   conf lib: read: 'voice_devices '
12/19 23:11:00 SS0   conf lib: read: 'dialout_timeout 90'
12/19 23:11:00 SS0   conf lib: read: 'ringback_goes_away 70'
12/19 23:11:00 SS0   conf lib: read: 'ringback_never_came 100'
12/19 23:11:00 SS0   conf lib: read: 'program pvf'
12/19 23:11:00 SS0   conf lib: read: 'port ttyS_ESS0'
12/19 23:11:00 SS0   section: port ttyS_ESS0, **found**
12/19 23:11:00 SS0   conf lib: read: 'ring_type ring'
12/19 23:11:00 SS0   found CT_KEYWORD ring_type ring
12/19 23:11:00 SS0   key: 'part', type=6, flags=4, data=(ignored)
12/19 23:11:00 SS0   key: 'program', type=6, flags=4, data=(ignored)
12/19 23:11:00 SS0   key: 'port', type=6, flags=4, data=(ignored)
12/19 23:11:00 SS0   key: 'ring_type', type=6, flags=4, data=(ignored)
12/19 23:11:00 SS0   key: 'voice_log_level', type=0, flags=3, data=8
12/19 23:11:00 SS0   key: 'voice_shell_log', type=1, flags=3, data=/var/log/vgetty_voice_shell.%s
12/19 23:11:00 SS0   key: 'voice_shell', type=1, flags=3, data=/bin/sh
12/19 23:11:00 SS0   key: 'port_speed', type=0, flags=3, data=115200
12/19 23:11:00 SS0   key: 'port_timeout', type=0, flags=3, data=10
12/19 23:11:00 SS0   key: 'dial_timeout', type=0, flags=3, data=90
12/19 23:11:00 SS0   key: 'command_delay', type=0, flags=3, data=100
12/19 23:11:00 SS0   key: 'dtmf_len', type=0, flags=3, data=30
12/19 23:11:00 SS0   key: 'dtmf_threshold', type=0, flags=3, data=40
12/19 23:11:00 SS0   key: 'dtmf_wait', type=0, flags=3, data=7
12/19 23:11:00 SS0   key: 'ignore_fax_dle', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'raw_data', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'rec_compression', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'rec_speed', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'rec_silence_len', type=0, flags=3, data=70
12/19 23:11:00 SS0   key: 'rec_silence_threshold', type=0, flags=3, data=40
12/19 23:11:00 SS0   key: 'rec_remove_silence', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'rec_max_len', type=0, flags=3, data=300
12/19 23:11:00 SS0   key: 'rec_min_len', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'do_hard_flow', type=3, flags=3, data=TRUE
12/19 23:11:00 SS0   key: 'force_autodetect', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'watchdog_timeout', type=0, flags=3, data=60
12/19 23:11:00 SS0   key: 'receive_gain', type=0, flags=3, data=-1
12/19 23:11:00 SS0   key: 'transmit_gain', type=0, flags=3, data=-1
12/19 23:11:00 SS0   key: 'enable_command_echo', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'poll_interval', type=0, flags=3, data=10
12/19 23:11:00 SS0   key: 'forceV253', type=3, flags=3, data=TRUE
12/19 23:11:00 SS0   key: 'forceV253subset', type=3, flags=1, data=FALSE
12/19 23:11:00 SS0   key: 'enable_compression_mapping_querry', type=3, flags=3, data=TRUE
12/19 23:11:00 SS0   key: 'compression_8bit_linear_signed', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'compression_16bit_linear_signed', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'compression_8bit_linear_unsigned', type=0, flags=3, data=1
12/19 23:11:00 SS0   key: 'compression_8bit_ulaw', type=0, flags=3, data=4
12/19 23:11:00 SS0   key: 'compression_8bit_alaw', type=0, flags=3, data=5
12/19 23:11:00 SS0   key: 'compression_2bit_adpcm', type=0, flags=3, data=140
12/19 23:11:00 SS0   key: 'compression_4bit_adpcm', type=0, flags=3, data=141
12/19 23:11:00 SS0   key: 'compression_4bit_ima_adpcm', type=0, flags=3, data=129
12/19 23:11:00 SS0   key: 'rings', type=1, flags=3, data=3
12/19 23:11:00 SS0   key: 'answer_mode', type=1, flags=3, data=voice:fax:data
12/19 23:11:00 SS0   key: 'toll_saver_rings', type=0, flags=3, data=0
12/19 23:11:00 SS0   key: 'rec_always_keep', type=3, flags=3, data=TRUE
12/19 23:11:00 SS0   key: 'voice_dir', type=1, flags=3, data=/var/spool/voice
12/19 23:11:00 SS0   key: 'phone_owner', type=1, flags=3, data=root
12/19 23:11:00 SS0   key: 'phone_group', type=1, flags=3, data=voice
12/19 23:11:00 SS0   key: 'phone_mode', type=0, flags=3, data=432
12/19 23:11:00 SS0   key: 'message_flag_file', type=1, flags=3, data=.flag
12/19 23:11:00 SS0   key: 'receive_dir', type=1, flags=3, data=incoming
12/19 23:11:00 SS0   key: 'message_dir', type=1, flags=3, data=messages
12/19 23:11:00 SS0   key: 'message_list', type=1, flags=3, data=Index
12/19 23:11:00 SS0   key: 'backup_message', type=1, flags=3, data=standard.rmd
12/19 23:11:00 SS0   key: 'button_program', type=1, flags=1, data=
12/19 23:11:00 SS0   key: 'call_program', type=1, flags=3, data=/home/user/say_callerid.sh
12/19 23:11:00 SS0   key: 'dtmf_program', type=1, flags=3, data=dtmf.sh
12/19 23:11:00 SS0   key: 'message_program', type=1, flags=1, data=
12/19 23:11:00 SS0   key: 'do_message_light', type=3, flags=3, data=FALSE
12/19 23:11:00 SS0   key: 'pre_message', type=1, flags=1, data=
12/19 23:11:00 SS0   key: 'beepsound', type=1, flags=1, data=
12/19 23:11:00 SS0   key: 'beep_frequency', type=0, flags=3, data=933
12/19 23:11:00 SS0   key: 'beep_length', type=0, flags=3, data=1500
12/19 23:11:00 SS0   key: 'max_tries', type=0, flags=3, data=3
12/19 23:11:00 SS0   key: 'retry_delay', type=0, flags=3, data=5
12/19 23:11:00 SS0   key: 'dialout_timeout', type=0, flags=1, data=90
12/19 23:11:00 SS0   key: 'ringback_goes_away', type=0, flags=1, data=70
12/19 23:11:00 SS0   key: 'ringback_never_came', type=0, flags=1, data=100
12/19 23:11:00 SS0   key: 'ring_report_delay', type=0, flags=3, data=15
12/19 23:11:00 SS0   key: 'voice_devices', type=1, flags=1, data=
12/19 23:11:00 SS0  check for lockfiles
12/19 23:11:00 SS0   checklock: stat failed, no file
12/19 23:11:00 SS0  locking the line
12/19 23:11:00 SS0   makelock(ttyS_ESS0) called
12/19 23:11:00 SS0   do_makelock: lock='/var/lock/LCK..ttyS_ESS0'
12/19 23:11:00 SS0   lock made
12/19 23:11:02 SS0   tio_get_rs232_lines: status: RTS CTS DSR DTR
12/19 23:11:02 SS0  lowering DTR to reset Modem
12/19 23:11:02 SS0   tss: set speed to 115200 (10002)
12/19 23:11:02 SS0   tio_set_flow_control( HARD )
12/19 23:11:02 SS0   waiting for line to clear (VTIME=1), read: 
12/19 23:11:02 SS0  send: AT#CID=1[0d]
12/19 23:11:02 SS0  waiting for ``OK''
12/19 23:11:02 SS0   got: AT#CID=1[0d]
12/19 23:11:02 SS0    CND: AT#CID=1[0d][0a]OK ** found **
12/19 23:11:03 SS0  mdm_send: 'ATI'
12/19 23:11:03 SS0    got:[0d][0a]ATI[0d]
12/19 23:11:03 SS0    got:[0d][0a]56000/33600[0d]
12/19 23:11:03 SS0   mdm_gis: string 1: '56000/33600'
12/19 23:11:03 SS0    got:[0a][0d][0a]OK[0d]
12/19 23:11:03 SS0   mdm_identify: string '56000/33600'
12/19 23:11:03 SS0  non-numeric ID string: '56000/33600'
12/19 23:11:03 SS0  mdm_send: 'AT+FCLASS=2.0'
12/19 23:11:03 SS0    got:[0a]AT+FCLASS=2.0[0d]
12/19 23:11:03 SS0   mdm_command: string 'AT+FCLASS=2.0'
12/19 23:11:03 SS0    got:[0d][0a]ERROR[0d]
12/19 23:11:03 SS0   mdm_command: string 'ERROR' -> ERROR
12/19 23:11:03 SS0  mdm_send: 'AT+FCLASS=2'
12/19 23:11:03 SS0    got:[0a]AT+FCLASS=2[0d]
12/19 23:11:03 SS0   mdm_command: string 'AT+FCLASS=2'
12/19 23:11:03 SS0    got:[0d][0a]OK[0d]
12/19 23:11:03 SS0   mdm_command: string 'OK' -> OK
12/19 23:11:03 SS0  mdm_send: 'AT+FCLASS=0'
12/19 23:11:03 SS0    got:[0a]AT+FCLASS=0[0d]
12/19 23:11:03 SS0   mdm_command: string 'AT+FCLASS=0'
12/19 23:11:03 SS0    got:[0d][0a]OK[0d]
12/19 23:11:03 SS0   mdm_command: string 'OK' -> OK
12/19 23:11:03 SS0  mdm_send: 'AT+FAA=1;+FCR=1'
12/19 23:11:03 SS0    got:[0a]AT+FAA=1;+FCR=1[0d]
12/19 23:11:03 SS0   mdm_command: string 'AT+FAA=1;+FCR=1'
12/19 23:11:03 SS0    got:[0d][0a]OK[0d]
12/19 23:11:03 SS0   mdm_command: string 'OK' -> OK
12/19 23:11:03 SS0  mdm_send: 'AT+FBOR=0'
12/19 23:11:03 SS0    got:[0a]AT+FBOR=0[0d]
12/19 23:11:03 SS0   mdm_command: string 'AT+FBOR=0'
12/19 23:11:03 SS0    got:[0d][0a]OK[0d]
12/19 23:11:03 SS0   mdm_command: string 'OK' -> OK
12/19 23:11:03 SS0  mdm_send: 'AT+FLID=" "'
12/19 23:11:03 SS0    got:[0a]AT+FLID=" "[0d]
12/19 23:11:03 SS0   mdm_command: string 'AT+FLID=" "'
12/19 23:11:03 SS0    got:[0d][0a]OK[0d]
12/19 23:11:03 SS0   mdm_command: string 'OK' -> OK
12/19 23:11:03 SS0  mdm_send: 'AT+FDCC=1,5,0,2,0,0,0,0'
12/19 23:11:03 SS0    got:[0a]AT+FDCC=1,5,0,2,0,0,0,0[0d]
12/19 23:11:03 SS0   mdm_command: string 'AT+FDCC=1,5,0,2,0,0,0,0'
12/19 23:11:03 SS0    got:[0d][0a]OK[0d]
12/19 23:11:03 SS0   mdm_command: string 'OK' -> OK
12/19 23:11:03 SS0   tss: set speed to 115200 (10002)
12/19 23:11:03 SS0   tss: set speed to 115200 (10002)
12/19 23:11:03 SS0   tio_set_flow_control( HARD )
12/19 23:11:03 SS0  detecting voice modem type
12/19 23:11:03 SS0    vgetty: ATE0
12/19 23:11:03 SS0    serial port: ATE0
12/19 23:11:03 SS0    serial port: OK
12/19 23:11:04 SS0   voice command: 'ATI9' -> ''
12/19 23:11:04 SS0    vgetty: ATI9
12/19 23:11:04 SS0    serial port: Data/Fax
12/19 23:11:04 SS0   V253 forced
12/19 23:11:04 SS0  V253 modem detected
12/19 23:11:04 SS0   voice modem type was set by ATI9 partial match
12/19 23:11:04 SS0    V253 modem: OK
12/19 23:11:04 SS0   vgetty: entering voice mode
12/19 23:11:04 SS0   vgetty: Installing signal handlers
12/19 23:11:04 SS0   voice command: 'AT+FCLASS?' -> ''
12/19 23:11:04 SS0    vgetty: AT+FCLASS?
12/19 23:11:04 SS0    V253 modem: 0
12/19 23:11:04 SS0   voice command: '' -> 'OK'
12/19 23:11:04 SS0    V253 modem: OK
12/19 23:11:04 SS0   voice command: 'AT+FCLASS=8' -> 'OK'
12/19 23:11:04 SS0    vgetty: AT+FCLASS=8
12/19 23:11:04 SS0    V253 modem: OK
12/19 23:11:04 SS0   voice command: 'AT' -> 'OK'
12/19 23:11:04 SS0    vgetty: AT
12/19 23:11:04 SS0    V253 modem: OK
12/19 23:11:04 SS0    vgetty: queued event RESET_WATCHDOG at position 0000
12/19 23:11:04 SS0  initializing V253 voice modem
12/19 23:11:04 SS0   voice command: 'AT+FCLASS=8' -> 'OK'
12/19 23:11:05 SS0    vgetty: AT+FCLASS=8
12/19 23:11:05 SS0    vgetty: unqueued event RESET_WATCHDOG at position 0000
12/19 23:11:05 SS0    vgetty: voice_handle_event got event RESET_WATCHDOG with data <NUL>
12/19 23:11:05 SS0    V253 modem: OK
12/19 23:11:05 SS0   voice command: 'AT+VSM=?' -> ''
12/19 23:11:05 SS0    vgetty: AT+VSM=?
12/19 23:11:05 SS0    V253 modem: 0,"SIGNED PCM",16,0,(8000),(127-129),(0-255)
12/19 23:11:05 SS0   Mapped signed PCM, 12 -> 0
12/19 23:11:05 SS0    V253 modem: 5,"A-Law Companded PCM",8,0,(8000),(127-129),(0-255)
12/19 23:11:05 SS0   Unknown: 5,"A-Law Companded PCM",8,0,(8000),(127-129),(0-255)
12/19 23:11:05 SS0    V253 modem: OK
12/19 23:11:05 SS0   Unknown: OK
12/19 23:11:05 SS0   voice command: 'AT+VSD=40,70' -> 'OK'
12/19 23:11:05 SS0    vgetty: AT+VSD=40,70
12/19 23:11:05 SS0    V253 modem: OK
12/19 23:11:05 SS0   voice command: 'AT+VGT=127' -> 'OK'
12/19 23:11:05 SS0    vgetty: AT+VGT=127
12/19 23:11:05 SS0    V253 modem: OK
12/19 23:11:05 SS0   voice command: 'AT+VGR=127' -> 'OK'
12/19 23:11:05 SS0    vgetty: AT+VGR=127
12/19 23:11:05 SS0    V253 modem: OK
12/19 23:11:05 SS0   voice command: 'AT+VRA=70;+VRN=10' -> 'OK'
12/19 23:11:05 SS0    vgetty: AT+VRA=70;+VRN=10
12/19 23:11:05 SS0    V253 modem: OK
12/19 23:11:05 SS0   voice command: 'AT+IFC=2,2' -> 'OK'
12/19 23:11:05 SS0    vgetty: AT+IFC=2,2
12/19 23:11:05 SS0    V253 modem: OK
12/19 23:11:05 SS0   tio_set_flow_control( HARD )
12/19 23:11:05 SS0   voice command: 'AT+VCID=1' -> 'OK'
12/19 23:11:05 SS0    vgetty: AT+VCID=1
12/19 23:11:05 SS0    V253 modem: OK
12/19 23:11:05 SS0   voice command: 'AT+VNH=0' -> 'OK'
12/19 23:11:05 SS0    vgetty: AT+VNH=0
12/19 23:11:05 SS0    V253 modem: OK
12/19 23:11:05 SS0   voice command: 'AT+VIT=0' -> 'OK'
12/19 23:11:06 SS0    vgetty: AT+VIT=0
12/19 23:11:06 SS0    V253 modem: OK
12/19 23:11:06 SS0   voice command: 'AT+VDR=1,15' -> 'OK'
12/19 23:11:06 SS0    vgetty: AT+VDR=1,15
12/19 23:11:06 SS0    V253 modem: OK
12/19 23:11:06 SS0   vgetty: leaving voice mode
12/19 23:11:06 SS0   voice command: 'AT+FCLASS=0' -> 'OK'
12/19 23:11:06 SS0    vgetty: AT+FCLASS=0
12/19 23:11:06 SS0    V253 modem: OK
12/19 23:11:06 SS0   voice command: 'AT' -> 'OK'
12/19 23:11:06 SS0    vgetty: AT
12/19 23:11:06 SS0    V253 modem: OK
12/19 23:11:06 SS0   vgetty: Restoring signal handlers
12/19 23:11:06 SS0   waiting for line to clear (VTIME=3), read: 
12/19 23:11:06 SS0   removing lock file
12/19 23:11:06 SS0  waiting...

```

---

### Post by HectorG on 2010-01-01
I have narrowed it down to it being the AT#CID=1 command that kills it.  Any Ideas?

If I start up mgetty without the port configured and call then let it ring, I then configure the port and start it up it works.. What could the problem be?

The modem is an ESS 2898

---

