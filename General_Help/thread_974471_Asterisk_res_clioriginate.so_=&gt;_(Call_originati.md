---
title: "Asterisk res_clioriginate.so =&gt; (Call origination from the CLI) Segmentation fault"
date: 2008-11-07
forum: General Help
---

### Post by borillionstar on 2008-11-07
I installed asterisk using apt-get when I start asterisk with the command asterisk -cv I get this:

telephone@telephonePBX:~$ sudo asterisk -cv
Asterisk 1.4.21.2~dfsg-1ubuntu3, Copyright (C) 1999 - 2008 Digium, Inc. and others.
Created by Mark Spencer <markster@digium.com>
Asterisk comes with ABSOLUTELY NO WARRANTY; type 'core show warranty' for details.
This is free software, with components licensed under the GNU General Public
License version 2 and other licenses; you are welcome to redistribute it under
certain conditions. Type 'core show license' for details.
=========================================================================
This package has been modified for the Debian GNU/Linux distribution
Please report all bugs to [http://bugs.debian.org/asterisk](http://bugs.debian.org/asterisk)
=========================================================================
Warning! Asterisk is not thread safe.
Asterisk Event Logger Started /var/log/asterisk/event_log
Asterisk Dynamic Loader Starting:
Asterisk Management interface listening on port 5038
[Nov  7 12:21:23] NOTICE[5287]: cdr.c:1373 do_reload: CDR simple logging enabled.
Asterisk PBX Core Initializing
Registering builtin applications:
 [Answer]
 [BackGround]
 [Busy]
 [Congestion]
 [Goto]
 [GotoIf]
 [GotoIfTime]
 [ExecIfTime]
 [Hangup]
 [NoOp]
 [Progress]
 [ResetCDR]
 [Ringing]
 [SayNumber]
 [SayDigits]
 [SayAlpha]
 [SayPhonetic]
 [SetAMAFlags]
 [SetGlobalVar]
 [Set]
 [ImportVar]
 [Wait]
 [WaitExten]
Asterisk Dynamic Loader Starting:
[Nov  7 12:21:23] NOTICE[5287]: loader.c:859 load_modules: 160 modules will be loaded.
res_musiconhold.so => (Music On Hold Resource)
res_watchdog.so => (Watchdog Resource)
app_pickup.so => (PickUp/PickDown/Steal/PickupChan/StealChan)
[Nov  7 12:21:23] NOTICE[5287]: res_odbc.c:235 load_odbc_config: Adding ENV var: INFORMIXSERVER=my_special_database
[Nov  7 12:21:23] NOTICE[5287]: res_odbc.c:235 load_odbc_config: Adding ENV var: INFORMIXDIR=/opt/informix
[Nov  7 12:21:23] NOTICE[5287]: res_odbc.c:716 load_module: res_odbc loaded.
res_odbc.so => (ODBC Resource)
 Loading [Sub]Agent Module
res_snmp.so => (SNMP [Sub]Agent for Asterisk)
res_agi.so => (Asterisk Gateway Interface (AGI))
res_esel.so => (Extension State Export Logic (E.S.E.L.) Resource)
res_monitor.so => (Call Monitoring Resource)
res_speech.so => (Generic Speech Recognition API)
res_features.so => (Call Features Resource)
[Nov  7 12:21:23] WARNING[5287]: res_smdi.c:1335 load_module: No SMDI interfaces are available to listen on, not starting SMDI listener.
res_indications.so => (Indications Resource)
app_segfault.so => (Application for crashing Asterisk with a segmentation fault)
res_adsi.so => (ADSI Resource)
res_jabber.so => (AJI - Asterisk Jabber Interface)
res_crypto.so => (Cryptographic Digital Signatures)
app_ices.so => (Encode and Stream via icecast and ices)
app_echo.so => (Simple Echo Application)
app_dictate.so => (Virtual Dictation Machine)
app_queue.so => (True Call Queueing)
func_uri.so => (URI encode/decode dialplan functions)
app_readfile.so => (Stores output of file into a variable)
app_adsiprog.so => (Asterisk ADSI Programming Application)
app_disa.so => (DISA (Direct Inward System Access) Application)
app_waitforring.so => (Waits until first ring after time)
codec_ulaw.so => (mu-Law Coder/Decoder)
app_senddtmf.so => (Send DTMF digits Application)
codec_speex.so => (Speex Coder/Decoder)
codec_lpc10.so => (LPC10 2.4kbps Coder/Decoder)
format_h263.so => (Raw H.263 data)
app_morsecode.so => (Morse code)
app_sendtext.so => (Send Text Applications)
cdr_radius.so => (RADIUS CDR Backend)
app_stack.so => (Stack Routines)
func_md5.so => (MD5 digest dialplan functions)
app_macro.so => (Extension Macros)
func_odbc.so => (ODBC lookups)
codec_adpcm.so => (Adaptive Differential PCM Coder/Decoder)
app_voicemail.so => (Comedian Mail (Voicemail System))
app_zapbarge.so => (Barge in on Zap channel application)
app_alarmreceiver.so => (Alarm Receiver for Asterisk)
app_dial.so => (Dialing Application)
func_env.so => (Environment/filesystem dialplan functions)
app_zapateller.so => (Block Telemarketers with Special Information Tone)
app_softhangup.so => (Hangs up the requested channel)
app_test.so => (Interface Test Application)
format_vox.so => (Dialogic VOX (ADPCM) File Format)
format_wav.so => (Microsoft WAV format (8000Hz Signed Linear))
app_zapscan.so => (Scan Zap channels application)
func_sha1.so => (SHA-1 computation dialplan function)
app_playback.so => (Sound File Playback Application)
format_h264.so => (Raw H.264 data)
app_url.so => (Send URL Applications)
pbx_config.so => (Text Extension Configuration)
func_math.so => (Mathematical dialplan function)
app_random.so => (Random goto)
app_db.so => (Database Access Functions)
func_base64.so => (base64 encode/decode dialplan functions)
chan_mgcp.so => (Media Gateway Control Protocol (MGCP))
chan_gtalk.so => (Gtalk Channel Driver)
chan_sip.so => (Session Initiation Protocol (SIP))
chan_zap.so => (Zapata Telephony)
func_devstate.so => (Gets or sets a device state in the dialplan)
pbx_dundi.so => (Distributed Universal Number Discovery (DUNDi))
app_amd.so => (Answering Machine Detection Application)
app_exec.so => (Executes dialplan applications)
app_dumpchan.so => (Dump Info About The Calling Channel)
func_global.so => (Global variable dialplan functions)
func_logic.so => (Logical dialplan functions)
codec_a_mu.so => (A-law and Mulaw direct Coder/Decoder)
func_groupcount.so => (Channel group dialplan functions)
app_directed_pickup.so => (Directed Call Pickup Application)
chan_phone.so => (Linux Telephony API Support)
app_nbscat.so => (Silly NBS Stream Application)
format_g726.so => (Raw G.726 (16/24/32/40kbps) data)
app_sms.so => (SMS/PSTN handler)
format_g729.so => (Raw G729 data)
app_system.so => (Generic System() application)
app_followme.so => (Find-Me/Follow-Me Application)
app_page.so => (Page Multiple Phones)
app_controlplayback.so => (Control Playback Application)
app_talkdetect.so => (Playback with Talk Detection)
chan_local.so => (Local Proxy Channel (Note: used internally by other modules))
func_rand.so => (Random number dialplan function)
codec_g726.so => (ITU G.726-32kbps G726 Transcoder)
func_channel.so => (Channel information dialplan function)
app_externalivr.so => (External IVR Interface Application)
app_festival.so => (Simple Festival Interface)
format_pcm.so => (Raw/Sun uLaw/ALaw 8KHz (PCM,PCMA,AU), G.722 16Khz)
app_record.so => (Trivial Record Application)
format_wav_gsm.so => (Microsoft WAV format (Proprietary GSM))
pbx_spool.so => (Outgoing Spool Support)
app_getcpeid.so => (Get ADSI CPE ID)
[Nov  7 12:21:23] WARNING[5287]: chan_iax2.c:11115 load_module: Unable to open IAX timing interface: No such file or directory
chan_iax2.so => (Inter Asterisk eXchange (Ver 2))
func_db.so => (Database (astdb) related dialplan functions)
cdr_custom.so => (Customizable Comma Separated Values CDR Backend)
format_jpeg.so => (JPEG (Joint Picture Experts Group) Image Format)
app_directory.so => (Extension Directory)
app_flash.so => (Flash channel application)
app_parkandannounce.so => (Call Parking and Announce Application)
app_read.so => (Read Variable Application)
cdr_csv.so => (Comma Separated Values CDR Backend)
app_channelredirect.so => (Channel Redirect)
app_while.so => (While Loops and Conditional Execution)
app_zapras.so => (Zap RAS Application)
app_lookupblacklist.so => (Look up Caller*ID name/number from blacklist database)
app_authenticate.so => (Authentication Application)
pbx_loopback.so => (Loopback Switch)
app_chanspy.so => (Listen to the audio of an active channel)
codec_alaw.so => (A-law Coder/Decoder)
format_sln.so => (Raw Signed Linear Audio support (SLN))
app_sayunixtime.so => (Say time)
app_cdr.so => (Tell Asterisk to not maintain a CDR for the current call)
  == No hardware transcoders found.
codec_zap.so => (Generic Zaptel Transcoder Codec Translator)
func_enum.so => (ENUM related dialplan functions)
func_strings.so => (String handling dialplan functions)
app_devstate.so => (Simple Devstate Application)
app_realtime.so => (Realtime Data Lookup/Rewrite)
cdr_pgsql.so => (PostgreSQL CDR Backend)
func_cdr.so => (CDR dialplan function)
app_mp3.so => (Silly MP3 Application)
app_mixmonitor.so => (Mixed Audio Monitoring Application)
[Nov  7 12:21:23] NOTICE[5287]: pbx_ael.c:4131 pbx_load_module: Starting AEL load process.
[Nov  7 12:21:23] NOTICE[5287]: pbx_ael.c:4138 pbx_load_module: AEL load process: calculated config file name '/etc/asterisk/extensions.ael'.
[Nov  7 12:21:23] NOTICE[5287]: pbx_ael.c:4146 pbx_load_module: AEL load process: parsed config file name '/etc/asterisk/extensions.ael'.
[Nov  7 12:21:23] NOTICE[5287]: pbx_ael.c:4149 pbx_load_module: AEL load process: checked config file name '/etc/asterisk/extensions.ael'.
[Nov  7 12:21:23] NOTICE[5287]: pbx_ael.c:4151 pbx_load_module: AEL load process: compiled config file name '/etc/asterisk/extensions.ael'.
[Nov  7 12:21:23] NOTICE[5287]: pbx_ael.c:4154 pbx_load_module: AEL load process: merged config file name '/etc/asterisk/extensions.ael'.
[Nov  7 12:21:23] NOTICE[5287]: pbx_ael.c:4157 pbx_load_module: AEL load process: verified config file name '/etc/asterisk/extensions.ael'.
pbx_ael.so => (Asterisk Extension Language Compiler)
res_clioriginate.so => (Call origination from the CLI)
Segmentation fault

The last line looks bad, is it running correctly? Also are there any good guides for setting asterisk up on ubuntu with the apt-get method?

Thanks
Bor

---

