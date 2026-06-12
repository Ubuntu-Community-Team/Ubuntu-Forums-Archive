---
title: "aMuleWeb"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by borobudur on 2009-10-04
Hi,
I'm trying to start aMuleWeb on my server but I can't connect to it. Everything seems to be fine but somewhere something is wrong.

Here the output of amuleweb and amuled:
```
myuser@mymachine:~$ amuled -o
amuled: OnInit - starting timer
Logging to stdout enabled
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
2009-10-04 20:56:10: ClientCreditsList.cpp(168): Creditfile loaded, 0 clients are known
2009-10-04 20:56:10: IPFilter.cpp(109): Loading IP-filters 'ipfilter.dat' and 'ipfilter_static.dat'.
2009-10-04 20:56:10: IPFilter.cpp(334): Loaded 0 IP-ranges from '/home/myuser/.aMule/ipfilter.dat'. 0 malformed lines were discarded.
2009-10-04 20:56:10: IPFilter.cpp(334): Loaded 0 IP-ranges from '/home/myuser/.aMule/ipfilter_static.dat'. 0 malformed lines were discarded.
2009-10-04 20:56:10: ServerList.cpp(83): Loading server.met file: /home/myuser/.aMule/server.met
2009-10-04 20:56:10: ServerList.cpp(168): 0 servers in server.met found
Loading temp files from /home/myuser/.aMule/Temp.

All PartFiles Loaded.
2009-10-04 20:56:10: DownloadQueue.cpp(173): No part files found
2009-10-04 20:56:10: ExternalConn.cpp(160): *** TCP socket (ECServer) listening on 0.0.0.0:4712
2009-10-04 20:56:10: MuleUDPSocket.cpp(78): Created Server UDP-Socket at port 4668
ListenSocket: Ok.

*** TCP socket (ECServer) listening on 0.0.0.0:4712
*** Server UDP socket (TCP+3) at 0.0.0.0:4668
*** TCP socket (TCP) listening on 0.0.0.0:4665
*** Client UDP socket (extended eMule) disabled on preferences
No shareable files found in directory: /home/myuser/.aMule/Incoming
2009-10-04 20:56:10: SharedFileList.cpp(353): Found 0 known shared files
2009-10-04 20:56:10: amule.cpp(784): Connecting
2009-10-04 20:56:10: ServerConnect.cpp(124): No valid servers to connect in serverlist found
2009-10-04 20:56:10: amule.cpp(2147): Kad network cannot be used if UDP port is disabled on preferences, not starting.
2009-10-04 20:56:11: amule.cpp(827): webserver running on pid 23553
2009-10-04 20:56:11: ThreadScheduler.cpp(308): ThreadScheduler: Completed task 'AICH Syncronizing', 0 tasks remaining.
2009-10-04 20:56:11: ExternalConn.cpp(218): New external connection accepted
2009-10-04 20:56:11: ExternalConn.cpp(252): Connecting client: aMuleweb SVN
2009-10-04 20:56:11: ExternalConn.cpp(302): Access granted.

``````
myuser@mymachine:~$ amuleweb -v
looking for template: php-default
checking for directory '/home/myuser/.aMule/webserver'... no
checking for directory '/usr/share/amule/webserver'... yes
checking for directory '/usr/share/amule/webserver/php-default'... yes
checking for file '/usr/share/amule/webserver/php-default/login.php'... yes
*** Using template: /usr/share/amule/webserver/php-default/aMule.tmpl
This is amuleweb SVN Mon Feb 18 07:02:15 CET 2008

Creating client...
Succeeded! Connection established to aMule SVN

--------------------------------------
|          aMule Web Server          |
--------------------------------------

Use 'Help' for command list

Web Server: Started

WSThread: Thread started
aMuleweb$ WSThread: created socket listening on :4711

```Just to show you the version:
```
myuser@mymachine:~$ amuled -v
amuled: OnInit - starting timer
aMuled SVN using wxGTK2 v2.8.7 (Snapshot: Mon Feb 18 07:02:15 CET 2008) (OS: Linux)

```Then the amule.conf file:
```
[eMule]
AppVersion=SVN
Nick=http://www.aMule.org
QueueSizePref=50
MaxUpload=0
MaxDownload=0
Port=4665
SlotAllocation=2
UDPPort=4672
UDPDisable=1
Address=
Autoconnect=1
MaxSourcesPerFile=300
MaxConnections=500
MaxConnectionsPerFiveSeconds=20
RemoveDeadServer=1
DeadServerRetry=2
ServerKeepAliveTimeout=0
Reconnect=1
Scoresystem=1
Serverlist=0
AddServersFromServer=1
AddServersFromClient=1
SafeServerConnect=0
AutoConnectStaticOnly=0
UPnPEnabled=0
UPnPTCPPort=50000
SmartIdCheck=1
ConnectToKad=1
ConnectToED2K=1
TempDir=/home/myuser/.aMule/Temp
IncomingDir=/home/myuser/.aMule/Incoming
ICH=1
AICHTrust=0
CheckDiskspace=1
MinFreeDiskSpace=1
AddNewFilesPaused=0
PreviewPrio=0
ManualHighPrio=0
FullChunkTransfers=1
StartNextFile=0
StartNextFileSameCat=0
FileBufferSizePref=16
DAPPref=1
UAPPref=1
OSDirectory=/home/myuser/.aMule/
OnlineSignature=0
OnlineSignatureUpdate=5
EnableTrayIcon=0
MinToTray=0
ConfirmExit=0
StartupMinimized=0
3DDepth=10
ToolTipDelay=1
ShowOverhead=0
ShowInfoOnCatTabs=0
ShowRatesOnTitle=0
VerticalToolbar=0
ShowPartFileNumber=0
VideoPlayer=
VideoPreviewBackupped=1
StatGraphsInterval=3
statsInterval=30
DownloadCapacity=3
UploadCapacity=3
StatsAverageMinutes=5
VariousStatisticsMaxValue=100
SeeShare=2
FilterLanIPs=1
ParanoidFiltering=1
IPFilterAutoLoad=1
IPFilterURL=
FilterLevel=127
IPFilterSystem=0
FilterMessages=0
FilterAllMessages=0
MessagesFromFriendsOnly=0
MessageFromValidSourcesOnly=1
FilterWordMessages=0
MessageFilter=
FilterComments=0
CommentFilter=
ShareHiddenFiles=0
AutoSortDownloads=0
NewVersionCheck=0
Language=
SplitterbarPosition=75
YourHostname=
DateTimeFormat=%A, %x, %X
IndicateRatings=1
AllcatType=0
ShowAllNotCats=0
DisableKnownClientList=0
DisableQueueList=0
MaxMessageSessions=50
SmartIdState=0
DropSlowSources=0
KadNodesUrl=http://emule-inside.net/nodes.dat
Ed2kServersUrl=http://gruk.org/server.met.gz
[FakeCheck]
Browser=0
BrowserTab=1
CustomBrowser=
[Proxy]
ProxyEnableProxy=0
ProxyType=0
ProxyName=
ProxyPort=1080
ProxyEnablePassword=0
ProxyUser=
ProxyPassword=
[WebServer]
Enabled=1
Password=946648xxxxxxxxxxxxxxxxxF581AA989540
PasswordLow=
WebUPnPTCPPort=50001
UPnPWebServerEnabled=0
UseGzip=1
UseLowRightsUser=0
PageRefreshTime=120
Template=
Port=4711
[ExternalConnect]
AcceptExternalConnections=1
ECAddress=
ECPort=4712
ECPassword=946648xxxxxxxxxxxxxxxxxF581AA989540
UPnPECEnabled=0
ShowProgressBar=1
ShowPercent=0
UseSecIdent=1
IpFilterClients=1
IpFilterServers=1
[Razor_Preferences]
FastED2KLinksHandler=1
[SkinGUIOptions]
UseSkinFiles=0
Skin=
[Statistics]
MaxClientVersions=0
TotalDownloadedBytes=0
TotalUploadedBytes=0
[Obfuscation]
IsClientCryptLayerSupported=1
IsCryptLayerRequested=1
IsClientCryptLayerRequired=0
CryptoPaddingLenght=254
CryptoKadUDPKey=-1299759614
[UserEvents]
[UserEvents/DownloadCompleted]
CoreEnabled=0
CoreCommand=
GUIEnabled=0
GUICommand=
[UserEvents/NewChatSession]
CoreEnabled=0
CoreCommand=
GUIEnabled=0
GUICommand=
[UserEvents/OutOfDiskSpace]
CoreEnabled=0
CoreCommand=
GUIEnabled=0
GUICommand=
[UserEvents/ErrorOnCompletion]
CoreEnabled=0
CoreCommand=
GUIEnabled=0
GUICommand=

```and remote.conf
```
Locale=
[EC]
Host=localhost
Port=4712
Password=946648xxxxxxxxxxxxxxxxxF581AA989540
[Webserver]
Port=-1
UPnPWebServerEnabled=0
UPnPTCPPort=50001
Template=php-default
UseGzip=0
AllowGuest=0
AdminPassword=946648xxxxxxxxxxxxxxxxxF581AA989540
GuestPassword=946648xxxxxxxxxxxxxxxxxF581AA989540

```

---

