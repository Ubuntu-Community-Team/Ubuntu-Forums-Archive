---
title: "HVR-2255 Capture Card Stopped Working"
date: 2015-02-24
forum: Hardware
---

### Post by bilkay on 2015-02-24
I finally got the card working, and I was trying to get Schedule Direct to work with Mythtv, and the card just stopped working. When I go to "Capture Cards" in setup, and select either of the cards, I get "Could not get card info for card ..... Unknown error" whereas before, it showed the card type. I tried deleting the card entries and creating new ones, but I get the same error.

Here's the output from `grep 7164 /var/log/dmesg` after rebooting:

```
[    0.168359] pci 0000:03:00.0: [1131:7164] type 00 class 0x048000
[   10.250867] saa7164 driver loaded
[   10.250973] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=11,autodetected]
[   10.250977] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 19, latency: 0, mmio: 0xf7800000
[   10.407209] saa7164_downloadfirmware() no first image
[   10.407220] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-04-01.1.fw)
[   10.685091] saa7164_downloadfirmware() firmware read 3283792 bytes.
[   10.685094] saa7164_downloadfirmware() firmware loaded.
[   10.685099] saa7164_downloadfirmware() SecBootLoader.FileSize = 3283792
[   10.685105] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   10.685105] saa7164_downloadfirmware() BSLSize = 0x0
[   10.685106] saa7164_downloadfirmware() Reserved = 0x0
[   10.685107] saa7164_downloadfirmware() Version = 0x1d21
```

Here's the backend log:

```
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I Logger logging.cpp:315 (run) Added logging to the console
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_CA.UTF-8
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Jupiter
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: E CoreContext configuration.cpp:107 (Save) Could not create /home/mythtv/.mythtv
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.
Feb 24 13:45:14 Jupiter mythbackend: mythbackend[2124]: E CoreContext tv_rec.cpp:1749 (GetStartChannel) TVRec[3]: Problem finding starting channel, setting to default of '3'.
Feb 24 13:45:15 Jupiter mythbackend: mythbackend[2124]: E CoreContext recorders/channelbase.cpp:944 (InitializeInputs) InitializeInputs(): #012#011#011#011Could not get inputs for the capturecard.#012#011#011#011Perhaps you have forgotten to bind video#012#011#011#011sources to your card's inputs?
Feb 24 13:45:15 Jupiter mythbackend: mythbackend[2124]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
Feb 24 13:45:15 Jupiter mythbackend: mythbackend[2124]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 3failed init
Feb 24 13:45:15 Jupiter mythbackend: mythbackend[2124]: E CoreContext tv_rec.cpp:1749 (GetStartChannel) TVRec[4]: Problem finding starting channel, setting to default of '3'.
Feb 24 13:45:15 Jupiter mythbackend: mythbackend[2124]: W CoreContext recorders/dvbchannel.cpp:229 (Open) DVBChan[4](/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.#012#011#011#011eno: Device or resource busy (16)
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[4](/dev/dvb/adapter1/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 4failed init
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: W CoreContext scheduler.cpp:213 (VerifyCards) Scheduler: Listings source '' is defined, but is not attached to a card input.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: W CoreContext scheduler.cpp:213 (VerifyCards) Scheduler: Listings source 'Schedules Direct' is defined, but is not attached to a card input.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext programinfo.cpp:2136 (CheckProgramIDAuthorities) Found 0 distinct programid authorities
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'LogClean'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'DBCleanup'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'ThemeUpdateNotifications'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'RecordedArtworkUpdate'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I Scheduler mythdbcon.cpp:436 (getStaticCon) New static DB connectionSchedCon
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'MythFillDB'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'JobQueueRecover'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'HardwareProfiler'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6544
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6544
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::468a:5bff:fece:50a8%eth1]:6544
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: N CoreContext mediaserver.cpp:168 (Init) MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext main_helpers.cpp:668 (run_backend) Main::Registering HttpStatus Extension
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6543
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6543
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::468a:5bff:fece:50a8%eth1]:6543
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Feb 24 13:45:19 Jupiter mythbackend: mythbackend[2124]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - SchedulerInit
Feb 24 13:45:20 Jupiter mythbackend: mythbackend[2124]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 19 items in 0.4 = 0.40 match + 0.04 check + 0.01 place
Feb 24 13:45:20 Jupiter mythbackend: mythbackend[2124]: I Scheduler scheduler.cpp:2278 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: Jupiter as a client (events: 0)
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: Jupiter as a client (events: 1)
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 4
Feb 24 13:46:35 Jupiter mythbackend: mythbackend[2124]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I Logger logging.cpp:315 (run) Added logging to the console
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_CA.UTF-8
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Jupiter
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: E CoreContext configuration.cpp:107 (Save) Could not create /home/mythtv/.mythtv
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to en_US
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale en_US
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Feb 24 13:45:07 Jupiter mythbackend: mythbackend[2124]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.
Feb 24 13:45:14 Jupiter mythbackend: mythbackend[2124]: E CoreContext tv_rec.cpp:1749 (GetStartChannel) TVRec[3]: Problem finding starting channel, setting to default of '3'.
Feb 24 13:45:15 Jupiter mythbackend: mythbackend[2124]: E CoreContext recorders/channelbase.cpp:944 (InitializeInputs) InitializeInputs(): #012#011#011#011Could not get inputs for the capturecard.#012#011#011#011Perhaps you have forgotten to bind video#012#011#011#011sources to your card's inputs?
Feb 24 13:45:15 Jupiter mythbackend: mythbackend[2124]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
Feb 24 13:45:15 Jupiter mythbackend: mythbackend[2124]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 3failed init
Feb 24 13:45:15 Jupiter mythbackend: mythbackend[2124]: E CoreContext tv_rec.cpp:1749 (GetStartChannel) TVRec[4]: Problem finding starting channel, setting to default of '3'.
Feb 24 13:45:15 Jupiter mythbackend: mythbackend[2124]: W CoreContext recorders/dvbchannel.cpp:229 (Open) DVBChan[4](/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.#012#011#011#011eno: Device or resource busy (16)
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: E CoreContext recorders/dvbchannel.cpp:234 (Open) DVBChan[4](/dev/dvb/adapter1/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: E CoreContext recorders/channelbase.cpp:1232 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: E CoreContext main_helpers.cpp:199 (setupTVs) Problem with capture cardsCard 4failed init
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: W CoreContext scheduler.cpp:213 (VerifyCards) Scheduler: Listings source '' is defined, but is not attached to a card input.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: W CoreContext scheduler.cpp:213 (VerifyCards) Scheduler: Listings source 'Schedules Direct' is defined, but is not attached to a card input.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext programinfo.cpp:2136 (CheckProgramIDAuthorities) Found 0 distinct programid authorities
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'LogClean'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'DBCleanup'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'ThemeUpdateNotifications'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'RecordedArtworkUpdate'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I Scheduler mythdbcon.cpp:436 (getStaticCon) New static DB connectionSchedCon
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'MythFillDB'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'JobQueueRecover'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'HardwareProfiler'.
Feb 24 13:45:16 Jupiter mythbackend: mythbackend[2124]: I CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6544
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6544
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::468a:5bff:fece:50a8%eth1]:6544
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: N CoreContext mediaserver.cpp:168 (Init) MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext main_helpers.cpp:668 (run_backend) Main::Registering HttpStatus Extension
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6543
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6543
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::468a:5bff:fece:50a8%eth1]:6543
Feb 24 13:45:17 Jupiter mythbackend: mythbackend[2124]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Feb 24 13:45:19 Jupiter mythbackend: mythbackend[2124]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - SchedulerInit
Feb 24 13:45:20 Jupiter mythbackend: mythbackend[2124]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 19 items in 0.4 = 0.40 match + 0.04 check + 0.01 place
Feb 24 13:45:20 Jupiter mythbackend: mythbackend[2124]: I Scheduler scheduler.cpp:2278 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: Jupiter as a client (events: 0)
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: Jupiter as a client (events: 1)
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 3
Feb 24 13:46:26 Jupiter mythbackend: mythbackend[2124]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 4
Feb 24 13:46:35 Jupiter mythbackend: mythbackend[2124]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

This line is strange:

```
Feb 24 13:45:15 Jupiter mythbackend: mythbackend[2124]: E CoreContext  recorders/channelbase.cpp:944 (InitializeInputs) InitializeInputs():  #012#011#011#011Could not get inputs for the  capturecard.#012#011#011#011Perhaps you have forgotten to bind  video#012#011#011#011sources to your card's inputs?
```

Since I don't have a video source I can use, I created one with no grabber (Name: Nil) and bound it to both cards. I tried using Schedules Direct, but found it didn't work. When I tried switching back is when the card stopped working. Judging from the log entry, could it be that the problem is a corrupted database? If so, how would I re-initialize it and start everything all over? The file /usr/share/mythtv/sql/mc.sql will dump the database and recreate it without any tables or data.

---

### Post by bilkay on 2015-02-25
It's not a hardware issue after all. I dumped the database and started all over and the card works. Contrary to what I said previously, /usr/share/mythtv/sql/mc.sql does not dump the database, it only creates it if it doesn't exist and sets up user 'mythtv'.

---

