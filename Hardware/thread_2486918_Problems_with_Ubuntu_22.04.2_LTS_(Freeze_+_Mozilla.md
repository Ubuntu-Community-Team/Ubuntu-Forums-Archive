---
title: "Problems with Ubuntu 22.04.2 LTS (Freeze + Mozilla Firefox crash tabs frequently)"
date: 2023-05-17
forum: Hardware
---

### Post by cioace9 on 2023-05-17
Hello community, last year I bought a new laptop with the following specifications:

Laptop Gaming ASUS ROG Strix G15 G513RC cu procesor AMD Ryzen™ 7 6800H, 15.6", Full HD, 144Hz, 8GB RAM DDR5, 512GB SSD, NVIDIA® GeForce RTX™ 3050 4GB, No OS, Eclipse Gray

And I upgraded the RAM memory from 8 to 32 GB. 

So far, everything works perfectly with the Windows 11 operating system, but on Ubuntu (and not only on Ubuntu, I tested several operating systems from the Linux range such as Arch Linux, Kali Linux, Linux Lite, etc.) having the same problem, the operating system after a short period of non-use it freezes and when I use mozilla firefox suddenly I get a crash (restore all tabs). I don't understand what's going on, I can't use Ubuntu because of this! I tried to install the video card from Nvidia using "Software & Updates" and I have the same problem! Please help me!

This log is from Mozilla Firefox:
_*Log1: *_
```
AdapterDeviceID: 0x25a2
AdapterDriverVendor: nvidia/unknown
AdapterDriverVersion: 525.105.17.0
AdapterVendorID: 0x10de
Add-ons: langpack-en-US%40firefox.mozilla.org:113.0.20230511.191846,%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D:3.17,clearcache%40michel.de.almeida:3.2,jid0-GXjLLfbCoAx0LcltEdFrEkQdQPI%40jetpack:4.3.7.9,formautofill%40mozilla.org:1.0.1,pictureinpicture%40mozilla.org:1.0.0,screenshots%40mozilla.org:39.0.1,webcompat%40mozilla.org:113.0.0,default-theme%40mozilla.org:1.3,addons-search-detection%40mozilla.com:2.0.0,google%40search.mozilla.org:1.4,amazondotcom%40search.mozilla.org:1.6,wikipedia%40search.mozilla.org:1.3,bing%40search.mozilla.org:1.5,ddg%40search.mozilla.org:1.4
AvailablePageFile: 13600231424
AvailablePhysicalMemory: 25250271232
AvailableSwapMemory: 6047133696
AvailableVirtualMemory: 27889299456
BackgroundTaskMode: 0
BuildID: 20230512012512
ContentSandboxCapabilities: 119
ContentSandboxCapable: 1
ContentSandboxLevel: 4
CrashTime: 1684218104
DOMFissionEnabled: 1
DOMIPCEnabled: 1
DesktopEnvironment: ubuntu:gnome
EMCheckCompatibility: true
EventLoopNestingLevel: 1
ExperimentalFeatures: accessibility.cache.enabled,devtools.inspector.compatibility.enabled
GpuSandboxLevel: 0
GraphicsNumActiveRenderers: 3
GraphicsNumRenderers: 3
HeadlessMode: 0
InstallTime: 1683966167
IsWayland: 0
LinuxUnderMemoryPressure: 0
Notes: FP(D00-L1000-W0000000-T010) Has dual GPUs. GPU #2: AdapterVendorID2: 0x1002, AdapterDeviceID2: 0x1681WR? WR+ EGL? EGL- GL Context? GL Context+ WebGL? WebGL+ 
ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
RDDProcessStatus: Running
ReleaseChannel: release
SafeMode: 0
SecondsSinceLastCrash: 25
StartupCrash: 0
StartupTime: 1684218082
SubmittedFrom: Client
TelemetryEnvironment: {"build":{"applicationId":"{ec8030f7-c20a-464f-9b0e-13a3a9e97384}","applicationName":"Firefox","architecture":"x86-64","buildId":"20230512012512","version":"113.0.1","vendor":"Mozilla","displayVersion":"113.0.1","platformVersion":"113.0.1","xpcomAbi":"x86_64-gcc3","updaterAvailable":false},"partner":{"distributionId":"canonical-002","distributionVersion":"1.0","partnerId":"ubuntu","distributor":"canonical","distributorChannel":"","partnerNames":["ubuntu"]},"system":{"memoryMB":31355,"virtualMaxMB":null,"cpu":{"extensions":["hasMMX","hasSSE","hasSSE2","hasSSE3","hasSSSE3","hasSSE4A","hasSSE4_1","hasSSE4_2","hasAVX","hasAVX2","hasAES"]},"os":{"name":"Linux","version":"5.19.0-41-generic","locale":"en-US"},"hdd":{"profile":{"model":null,"revision":null,"type":null},"binary":{"model":null,"revision":null,"type":null},"system":{"model":null,"revision":null,"type":null}},"gfx":{"D2DEnabled":null,"DWriteEnabled":null,"ContentBackend":"Skia","Headless":false,"EmbeddedInFirefoxReality":null,"adapters":[{"description":"NVIDIA GeForce RTX 3050 Laptop GPU/PCIe/SSE2","vendorID":"0x10de","deviceID":"0x25a2","subsysID":null,"RAM":0,"driver":null,"driverVendor":"nvidia/unknown","driverVersion":"525.105.17.0","driverDate":null,"GPUActive":true},{"description":null,"vendorID":"0x1002","deviceID":"0x1681","subsysID":null,"RAM":null,"driver":null,"driverVendor":null,"driverVersion":null,"driverDate":null,"GPUActive":false}],"monitors":[{"screenWidth":1920,"screenHeight":1080}],"features":{"compositor":"webrender","hwCompositing":{"status":"available"},"gpuProcess":{"status":"unused"},"webrender":{"status":"available"},"wrCompositor":{"status":"blocked:FEATURE_FAILURE_DISABLE_RELEASE_OR_BETA"},"openglCompositing":{"status":"available"},"omtp":{"status":"unused"}}},"appleModelId":null,"hasWinPackageId":null},"settings":{"blocklistEnabled":true,"e10sEnabled":true,"e10sMultiProcesses":8,"fissionEnabled":true,"telemetryEnabled":false,"locale":"en-US","intl":{"requestedLocales":["en-US"],"availableLocales":["en-US"],"appLocales":["en-US"],"systemLocales":["en-US"],"regionalPrefsLocales":["ro-RO"],"acceptLanguages":["en-US","en"]},"update":{"channel":"release","enabled":true,"autoDownload":false,"background":false},"userPrefs":{"browser.fixup.alternate.enabled":false,"browser.search.region":"RO","browser.search.widget.inNavBar":false,"browser.urlbar.autoFill":true,"browser.urlbar.autoFill.adaptiveHistory.enabled":false,"browser.urlbar.dnsResolveSingleWordsAfterSearch":0,"browser.urlbar.quicksuggest.dataCollection.enabled":false,"browser.urlbar.suggest.quicksuggest.nonsponsored":false,"browser.urlbar.suggest.quicksuggest.sponsored":false,"browser.urlbar.suggest.bestmatch":true,"media.gmp-gmpopenh264.lastInstallStart":1680436530,"media.gmp-gmpopenh264.lastDownload":1680436531,"media.gmp-gmpopenh264.lastUpdate":1680436531,"media.gmp-manager.lastCheck":1684145180,"media.gmp-manager.lastEmptyCheck":1684145180,"network.trr.strict_native_fallback":false,"widget.content.allow-gtk-dark-theme":false,"widget.content.gtk-high-contrast.enabled":true},"sandbox":{"effectiveContentProcessLevel":4,"contentWin32kLockdownState":3},"addonCompatibilityCheckEnabled":true,"isDefaultBrowser":false,"defaultSearchEngine":"google-ubuntu-sn","defaultSearchEngineData":{"loadPath":"[addon]google@search.mozilla.org","name":"Google","origin":"default","submissionURL":"https://www.google.com/search?channel=fs&client=ubuntu-sn&q="}},"profile":{"creationDate":19449,"firstUseDate":19449},"addons":{"activeAddons":{"clearcache@michel.de.almeida":{"version":"3.2","scope":1,"type":"extension","updateDay":19449,"isSystem":false,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Clear browser cache with a single click or via the F9 key.","name":"Clear Cache","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19449,"signedState":2},"jid0-GXjLLfbCoAx0LcltEdFrEkQdQPI@jetpack":{"version":"4.3.7.9","scope":1,"type":"extension","updateDay":19457,"isSystem":false,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Screen capture for all or part of any web page. Add annotations, comments, blur sensitive info, and ","name":"Awesome Screenshot: Screen capture, Annotate","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19457,"signedState":2},"langpack-en-US@firefox.mozilla.org":{"version":"113.0.20230511.191846","scope":1,"type":"locale","updateDay":19490,"isSystem":false,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Firefox Language Pack for English (US) (en-US)","name":"Language: English (US)","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19449,"signedState":2},"formautofill@mozilla.org":{"version":"1.0.1","scope":1,"type":"extension","updateDay":19489,"isSystem":true,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":null,"name":"Form Autofill","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19437},"pictureinpicture@mozilla.org":{"version":"1.0.0","scope":1,"type":"extension","updateDay":19489,"isSystem":true,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Fixes for web compatibility with Picture-in-Picture","name":"Picture-In-Picture","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19437},"screenshots@mozilla.org":{"version":"39.0.1","scope":1,"type":"extension","updateDay":19489,"isSystem":true,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Take clips and screenshots from the Web and save them temporarily or permanently.","name":"Firefox Screenshots","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19437},"webcompat@mozilla.org":{"version":"113.0.0","scope":1,"type":"extension","updateDay":19489,"isSystem":true,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Urgent post-release fixes for web compatibility.","name":"Web Compatibility Interventions","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19437},"{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}":{"version":"3.17","scope":1,"type":"extension","updateDay":19492,"isSystem":false,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Block YouTube™ ads, pop-ups & fight malware!","name":"Adblock Plus - free ad blocker","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19449,"signedState":2}},"theme":{"id":"default-theme@mozilla.org","blocklisted":false,"description":"Follow the operating system setting for buttons, menus, and windows.","name":"System theme — auto","userDisabled":false,"appDisabled":false,"version":"1.3","scope":4,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19449,"updateDay":19449},"activeGMPlugins":{"gmp-gmpopenh264":{"version":"1.8.1.2","userDisabled":false,"applyBackgroundUpdates":1}}},"experiments":{"next-generation-accessibility-engine-powering-screen-readers":{"branch":"treatment-a","type":"nimbus-rollout","enrollmentId":"94a348bd-619f-462e-a6bc-d3cf327b4c6b"},"abouthome-startup-cache-rollout":{"branch":"control","type":"nimbus-rollout","enrollmentId":"dcadf4e4-f931-4835-90ab-a74a0780cb63"}}}
Throttleable: 1
TotalPageFile: 38924988416
TotalPhysicalMemory: 32877854720
URL: [http://192.168.0.133:5000/v1/login](http://192.168.0.133:5000/v1/login)
UptimeTS: 21.88620662
UtilityProcessStatus: Running
Vendor: Mozilla
Version: 113.0.1
useragent_locale: en-US[B]
```

This report also contains technical information about the state of the application when it crashed.

[/B][I][U]Log2:
[/U][/I]```
AdapterDeviceID: 0x25a2
AdapterDriverVendor: nvidia/unknown
AdapterDriverVersion: 525.105.17.0
AdapterVendorID: 0x10de
Add-ons: langpack-en-US%40firefox.mozilla.org:113.0.20230511.191846,%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D:3.17,clearcache%40michel.de.almeida:3.2,jid0-GXjLLfbCoAx0LcltEdFrEkQdQPI%40jetpack:4.3.7.9,formautofill%40mozilla.org:1.0.1,pictureinpicture%40mozilla.org:1.0.0,screenshots%40mozilla.org:39.0.1,webcompat%40mozilla.org:113.0.0,default-theme%40mozilla.org:1.3,addons-search-detection%40mozilla.com:2.0.0,google%40search.mozilla.org:1.4,amazondotcom%40search.mozilla.org:1.6,wikipedia%40search.mozilla.org:1.3,bing%40search.mozilla.org:1.5,ddg%40search.mozilla.org:1.4
AvailablePageFile: 13358477312
AvailablePhysicalMemory: 24984846336
AvailableSwapMemory: 6047133696
AvailableVirtualMemory: 27666554880
BackgroundTaskMode: 0
BuildID: 20230512012512
ContentSandboxCapabilities: 119
ContentSandboxCapable: 1
ContentSandboxLevel: 4
CrashTime: 1684218217
DOMFissionEnabled: 1
DOMIPCEnabled: 1
DesktopEnvironment: ubuntu:gnome
EMCheckCompatibility: true
EventLoopNestingLevel: 1
ExperimentalFeatures: accessibility.cache.enabled,devtools.inspector.compatibility.enabled
GpuSandboxLevel: 0
GraphicsCriticalError: |[0][GFX1-]: VideoBridgeParent receives IPC close with reason=AbnormalShutdown (t=9.25196) 
GraphicsNumActiveRenderers: 4
GraphicsNumRenderers: 4
HeadlessMode: 0
InstallTime: 1683966167
IsWayland: 0
LastInteractionDuration: 10
LinuxUnderMemoryPressure: 0
Notes: FP(D00-L1000-W0000000-T010) Has dual GPUs. GPU #2: AdapterVendorID2: 0x1002, AdapterDeviceID2: 0x1681WR? WR+ EGL? EGL- GL Context? GL Context+ WebGL? WebGL+ 
ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
RDDProcessStatus: Running
ReleaseChannel: release
SafeMode: 0
SecondsSinceLastCrash: 71
StartupCrash: 0
StartupTime: 1684218148
SubmittedFrom: Client
TelemetryEnvironment: {"build":{"applicationId":"{ec8030f7-c20a-464f-9b0e-13a3a9e97384}","applicationName":"Firefox","architecture":"x86-64","buildId":"20230512012512","version":"113.0.1","vendor":"Mozilla","displayVersion":"113.0.1","platformVersion":"113.0.1","xpcomAbi":"x86_64-gcc3","updaterAvailable":false},"partner":{"distributionId":"canonical-002","distributionVersion":"1.0","partnerId":"ubuntu","distributor":"canonical","distributorChannel":"","partnerNames":["ubuntu"]},"system":{"memoryMB":31355,"virtualMaxMB":null,"cpu":{"count":16,"cores":8,"vendor":"AuthenticAMD","name":"AMD Ryzen 7 6800H with Radeon Graphics","family":25,"model":68,"stepping":1,"l2cacheKB":512,"l3cacheKB":16384,"speedMHz":4784,"extensions":["hasMMX","hasSSE","hasSSE2","hasSSE3","hasSSSE3","hasSSE4A","hasSSE4_1","hasSSE4_2","hasAVX","hasAVX2","hasAES"]},"os":{"name":"Linux","version":"5.19.0-41-generic","locale":"en-US"},"hdd":{"profile":{"model":null,"revision":null,"type":null},"binary":{"model":null,"revision":null,"type":null},"system":{"model":null,"revision":null,"type":null}},"gfx":{"D2DEnabled":null,"DWriteEnabled":null,"ContentBackend":"Skia","Headless":false,"EmbeddedInFirefoxReality":null,"adapters":[{"description":"NVIDIA GeForce RTX 3050 Laptop GPU/PCIe/SSE2","vendorID":"0x10de","deviceID":"0x25a2","subsysID":null,"RAM":0,"driver":null,"driverVendor":"nvidia/unknown","driverVersion":"525.105.17.0","driverDate":null,"GPUActive":true},{"description":null,"vendorID":"0x1002","deviceID":"0x1681","subsysID":null,"RAM":null,"driver":null,"driverVendor":null,"driverVersion":null,"driverDate":null,"GPUActive":false}],"monitors":[{"screenWidth":1920,"screenHeight":1080}],"features":{"compositor":"webrender","hwCompositing":{"status":"available"},"gpuProcess":{"status":"unused"},"webrender":{"status":"available"},"wrCompositor":{"status":"blocked:FEATURE_FAILURE_DISABLE_RELEASE_OR_BETA"},"openglCompositing":{"status":"available"},"omtp":{"status":"unused"}}},"appleModelId":null,"hasWinPackageId":null},"settings":{"blocklistEnabled":true,"e10sEnabled":true,"e10sMultiProcesses":8,"fissionEnabled":true,"telemetryEnabled":false,"locale":"en-US","intl":{"requestedLocales":["en-US"],"availableLocales":["en-US"],"appLocales":["en-US"],"systemLocales":["en-US"],"regionalPrefsLocales":["ro-RO"],"acceptLanguages":["en-US","en"]},"update":{"channel":"release","enabled":true,"autoDownload":false,"background":false},"userPrefs":{"browser.fixup.alternate.enabled":false,"browser.search.region":"RO","browser.search.widget.inNavBar":false,"browser.urlbar.autoFill":true,"browser.urlbar.autoFill.adaptiveHistory.enabled":false,"browser.urlbar.dnsResolveSingleWordsAfterSearch":0,"browser.urlbar.quicksuggest.dataCollection.enabled":false,"browser.urlbar.suggest.quicksuggest.nonsponsored":false,"browser.urlbar.suggest.quicksuggest.sponsored":false,"browser.urlbar.suggest.bestmatch":true,"media.gmp-gmpopenh264.lastInstallStart":1680436530,"media.gmp-gmpopenh264.lastDownload":1680436531,"media.gmp-gmpopenh264.lastUpdate":1680436531,"media.gmp-manager.lastCheck":1684145180,"media.gmp-manager.lastEmptyCheck":1684145180,"network.trr.strict_native_fallback":false,"widget.content.allow-gtk-dark-theme":false,"widget.content.gtk-high-contrast.enabled":true},"sandbox":{"effectiveContentProcessLevel":4,"contentWin32kLockdownState":3},"addonCompatibilityCheckEnabled":true,"isDefaultBrowser":false,"defaultSearchEngine":"google-ubuntu-sn","defaultSearchEngineData":{"loadPath":"[addon]google@search.mozilla.org","name":"Google","origin":"default","submissionURL":"https://www.google.com/search?channel=fs&client=ubuntu-sn&q="}},"profile":{"creationDate":19449,"firstUseDate":19449},"addons":{"activeAddons":{"clearcache@michel.de.almeida":{"version":"3.2","scope":1,"type":"extension","updateDay":19449,"isSystem":false,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Clear browser cache with a single click or via the F9 key.","name":"Clear Cache","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19449,"signedState":2},"jid0-GXjLLfbCoAx0LcltEdFrEkQdQPI@jetpack":{"version":"4.3.7.9","scope":1,"type":"extension","updateDay":19457,"isSystem":false,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Screen capture for all or part of any web page. Add annotations, comments, blur sensitive info, and ","name":"Awesome Screenshot: Screen capture, Annotate","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19457,"signedState":2},"langpack-en-US@firefox.mozilla.org":{"version":"113.0.20230511.191846","scope":1,"type":"locale","updateDay":19490,"isSystem":false,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Firefox Language Pack for English (US) (en-US)","name":"Language: English (US)","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19449,"signedState":2},"formautofill@mozilla.org":{"version":"1.0.1","scope":1,"type":"extension","updateDay":19489,"isSystem":true,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":null,"name":"Form Autofill","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19437},"pictureinpicture@mozilla.org":{"version":"1.0.0","scope":1,"type":"extension","updateDay":19489,"isSystem":true,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Fixes for web compatibility with Picture-in-Picture","name":"Picture-In-Picture","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19437},"screenshots@mozilla.org":{"version":"39.0.1","scope":1,"type":"extension","updateDay":19489,"isSystem":true,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Take clips and screenshots from the Web and save them temporarily or permanently.","name":"Firefox Screenshots","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19437},"webcompat@mozilla.org":{"version":"113.0.0","scope":1,"type":"extension","updateDay":19489,"isSystem":true,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Urgent post-release fixes for web compatibility.","name":"Web Compatibility Interventions","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19437},"{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}":{"version":"3.17","scope":1,"type":"extension","updateDay":19492,"isSystem":false,"isWebExtension":true,"multiprocessCompatible":true,"blocklisted":false,"description":"Block YouTube™ ads, pop-ups & fight malware!","name":"Adblock Plus - free ad blocker","userDisabled":false,"appDisabled":false,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19449,"signedState":2}},"theme":{"id":"default-theme@mozilla.org","blocklisted":false,"description":"Follow the operating system setting for buttons, menus, and windows.","name":"System theme — auto","userDisabled":false,"appDisabled":false,"version":"1.3","scope":4,"foreignInstall":false,"hasBinaryComponents":false,"installDay":19449,"updateDay":19449},"activeGMPlugins":{"gmp-gmpopenh264":{"version":"1.8.1.2","userDisabled":false,"applyBackgroundUpdates":1}}},"experiments":{"next-generation-accessibility-engine-powering-screen-readers":{"branch":"treatment-a","type":"nimbus-rollout","enrollmentId":"94a348bd-619f-462e-a6bc-d3cf327b4c6b"},"abouthome-startup-cache-rollout":{"branch":"control","type":"nimbus-rollout","enrollmentId":"dcadf4e4-f931-4835-90ab-a74a0780cb63"}}}
Throttleable: 1
TotalPageFile: 38924988416
TotalPhysicalMemory: 32877854720
URL: [https://www.youtube.com/]("https://www.youtube.com/watch?v=HTVum_K4Bp0")
UptimeTS: 68.53972848
UtilityProcessStatus: Running
Vendor: Mozilla
Version: 113.0.1
useragent_locale: en-US
```

**This report also contains technical information about the state of the application when it crashed.**


Last error from journal:
```
mai 16 22:03:59 dragos systemd[1]: whoopsie.service: Deactivated successfully.mai 16 22:04:07 dragos whoopsie-upload-all[9217]: INFO:root:All reports uploaded successfully
mai 16 22:04:07 dragos systemd[1]: apport-autoreport.service: Deactivated successfully.
mai 16 22:04:07 dragos systemd[1]: Finished Process error reports when automatic reporting is enabled.
mai 16 22:04:45 dragos dbus-daemon[3171]: [session uid=1000 pid=3171] Activating via systemd: service name='io.snapcraft.SessionAgent' unit='snapd.session-agent.service' requested by ':1.37' (uid=1000 p>
mai 16 22:04:45 dragos dbus-daemon[3171]: [session uid=1000 pid=3171] Successfully activated service 'io.snapcraft.SessionAgent'
mai 16 22:04:45 dragos systemd[3098]: Starting snapd user session agent...
mai 16 22:04:45 dragos systemd[3098]: Started snapd user session agent.
mai 16 22:04:45 dragos gnome-shell[4081]: Ignored exception from dbus method: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownInterface: Object does not implement the interface
mai 16 22:04:47 dragos dbus-daemon[3171]: [session uid=1000 pid=3171] Activating service name='org.gnome.Nautilus' requested by ':1.37' (uid=1000 pid=4081 comm="/usr/bin/gnome-shell " label="unconfined")
mai 16 22:04:47 dragos dbus-daemon[3171]: [session uid=1000 pid=3171] Successfully activated service 'org.gnome.Nautilus'
mai 16 22:04:47 dragos dbus-daemon[771]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.106' (uid=1000 pid=9265 >
mai 16 22:04:47 dragos systemd[1]: Starting Hostname Service...
mai 16 22:04:47 dragos dbus-daemon[771]: [system] Successfully activated service 'org.freedesktop.hostname1'
mai 16 22:04:47 dragos systemd[1]: Started Hostname Service.
mai 16 22:04:51 dragos gnome-shell[4081]: Failed to import DBusMenu, quicklists are not avaialble: Error: Requiring Dbusmenu, version none: Typelib file for namespace 'Dbusmenu' (any version) not found
mai 16 22:04:52 dragos systemd[3098]: Started Application launched by gnome-shell.
mai 16 22:04:52 dragos systemd[3098]: Started VTE child process 9296 launched by gnome-terminal-server process 5769.
mai 16 22:05:07 dragos systemd[3098]: Started Application launched by gnome-shell.
mai 16 22:05:07 dragos systemd[3098]: Started VTE child process 9322 launched by gnome-terminal-server process 5769.
mai 16 22:05:15 dragos snap[9243]: session_agent.go:329: read unix @->/run/user/1000/bus: use of closed network connection
mai 16 22:05:29 dragos systemd[1]: systemd-hostnamed.service: Deactivated successfully.
mai 16 22:05:35 dragos gnome-shell[4081]: Can't update stage views actor <unnamed>[<MetaWindowGroup>:0x55c3de4682f0] is on because it needs an allocation.
mai 16 22:05:35 dragos gnome-shell[4081]: Can't update stage views actor <unnamed>[<MetaWindowActorX11>:0x55c3e051dad0] is on because it needs an allocation.
mai 16 22:05:35 dragos gnome-shell[4081]: Can't update stage views actor <unnamed>[<MetaSurfaceActorX11>:0x55c3e0521130] is on because it needs an allocation.
mai 16 22:05:45 dragos /usr/libexec/gdm-x-session[3415]: (EE) event6  - Asus Keyboard: client bug: event processing lagging behind by 25ms, your system is too slow
mai 16 22:06:06 dragos systemd[3098]: gnome-terminal-server.service: Main process exited, code=killed, status=9/KILL
mai 16 22:06:06 dragos systemd[3098]: gnome-terminal-server.service: Failed with result 'signal'.
mai 16 22:06:15 dragos kernel: divide error: 0000 [#1] PREEMPT SMP NOPTI
mai 16 22:06:15 dragos kernel: CPU: 15 PID: 0 Comm: swapper/15 Not tainted 5.19.0-41-generic #42~22.04.1-Ubuntu
mai 16 22:06:15 dragos kernel: Hardware name: ASUSTeK COMPUTER INC. ROG Strix G513RC_G513RC/G513RC, BIOS G513RC.327 02/16/2023
mai 16 22:06:15 dragos kernel: RIP: 0010:__update_load_avg_cfs_rq+0x1ac/0x650
mai 16 22:06:15 dragos kernel: Code: 48 f7 f1 31 d2 49 89 84 24 a0 00 00 00 49 8b 84 24 90 00 00 00 48 f7 f1 31 d2 49 89 84 24 a8 00 00 00 41 8b 84 24 98 00 00 00 <f7> f1 49 89 84 24 b0 00 00 00 0f 1f 4>
mai 16 22:06:15 dragos kernel: RSP: 0018:ffff9d20c053ce10 EFLAGS: 00010046
mai 16 22:06:15 dragos kernel: RAX: 000000008000fa26 RBX: 0000000000000000 RCX: 000000000000b90d
mai 16 22:06:15 dragos kernel: RDX: 0000000000000000 RSI: 0000000000000003 RDI: 00000061c0ca3c8b
```

---

