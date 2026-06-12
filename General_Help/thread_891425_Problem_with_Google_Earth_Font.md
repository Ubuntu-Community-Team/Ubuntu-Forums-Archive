---
title: "Problem with Google Earth Font"
date: 2008-08-16
forum: General Help
---

### Post by Xero121690 on 2008-08-16
I just installed Google earth(new version) on Ubuntu and well the font is so small i cant see the options..
Can some one please help me. 
I tried 
> sudo $HOME/.config/Google/GoogleEarthPlus.conf

but it says command not found...

---

### Post by Dubbayoo on 2008-11-16
> **Xero121690 said:**
> I just installed Google earth(new version) on Ubuntu and well the font is so small i cant see the options..
Can some one please help me. 
I tried 


but it says command not found...
You're not telling the command what you want to DO with the file. 

sudo "MISSING COMMAND HERE" $HOME/.config/Google/GoogleEarthPlus.conf

My take is try this: sudo gedit $HOME/.config/Google/GoogleEarthPlus.conf 

change GuiFontSize=8 to GuiFontSize=12

I also found that if I run Google Earth from the Applications menu instead of the desktop icon that gets created things look better, even though that shouldn't make any difference.

---

### Post by oRioN84 on 2008-11-23
(Ubuntu 8.04) Generic Kernel
I'm having the same problem. Here is a screenshot of my desktop while Google Earth is loaded: [http://i69.photobucket.com/albums/i61/saycdrom/goog_earth.jpg]("http://i69.photobucket.com/albums/i61/saycdrom/goog_earth.jpg")


As you can see, it is unreadable. I tried the aforementioned solution of editing the conf file,
```
sudo $HOME/.config/Google/GoogleEarthPlus.conf
```

and here is the contents of that file:

```
[General]
AnimSpeed=1
CachePath=/root/.googleearth/Cache
ClampBegin=false
ControllerEnabled=false
ControllerMode=2
InvertMouseWheel=false
KMLPath=/root/.googleearth
Key="kWcxRnCHGkA="
LogoutClean=true
NavigatorShow=0
PolyEditXPos=50
PolyEditYPos=74
RepeatMode=1
ReverseControls=false
SMode=true
SwoopEnabled=true
TimeFolderRestrict=false
TimeShow=1
TimeZoneHours=-5
TimeZoneMinutes=0
TimeZoneMode=1
TimeZoneName=Local
UID="pVsXqIyAk9NVHAE/pzlCiA=="
VID="AAAADTQuMy43Mjg0LjM5MTY="
currentVersion=4.3.7284.3916
defaultBrowser=true
enableTips=true
hiddenWindows-4_3=@Invalid()
lastHeight=690
lastLeft=0
lastTip=2
lastTop=54
lastWidth=1360
layersOpen=true
mouseWheelSpeed=1
osName=Linux
placesOpen=true
renderWarning-OGLsoftwareEmulated=false
searchOpen=true
shown_GPS=false
shown_LeftPanel=true
shown_RenderFrame=true
shown_Ruler=false
visibleWindows-4_3=RenderWindow, ServerWindow
wasFullScreen=false
wasMaximized=true

[Layer]
FlySpeed=0.171
drivingDirectionsRange=1000
drivingDirectionsSpeed=150
drivingDirectionsTilt=45
pauseTime=1.6
tourBalloonShow=false
tourCycles=1
tourSpeed=0.171

[Render]
CompassVisible=true

[UsageStatistics]
firstRun\day=15
firstRun\hour=21
firstRun\minute=49
firstRun\month=11
firstRun\second=30
firstRun\year=2008
loginHistory=0
numRuns=1
numRunsThisVersion=1
prevRun\day=15
prevRun\hour=21
prevRun\minute=49
prevRun\month=11
prevRun\second=30
prevRun\year=2008

[autoupdate]
InstalledVersion=4.3.7284.3916
```

There is no line that says GuiFontSize=  so, I added it manually to the first section:

```
GuiFontSize=12
```

Yet, the problem remains regardless.

---

### Post by Roasted on 2008-12-07
I had this same problem and this thread has helped me.

I'm posting my conf file for Google Earth 4.3 after I changed the GuiFontSize to 12.

I suggest anybody who uses it to back up their existing conf file just in case. But this worked for me.

```
[General]
AnimSpeed=1
CachePath=/home/jason/.googleearth/Cache
ClampBegin=false
ControllerEnabled=false
ControllerMode=2
InvertMouseWheel=false
KMLPath=/home/jason/.googleearth
Key="zJHuP1U6z9M="
LogoutClean=false
NavMode=0
NavigatorShow=0
PolyEditXPos=70
PolyEditYPos=75
RepeatMode=1
ReverseControls=false
SMode=true
SwoopEnabled=true
TimeFolderRestrict=false
TimeShow=1
TimeZoneHours=-5
TimeZoneMinutes=0
TimeZoneMode=1
TimeZoneName=Local
UID="zAso55FA8A1HTcWHiOIKSA=="
UsageStats=false
VID="AAAADTQuMy43Mjg0LjM5MTY="
adsDisabled=false
buildingHighlight=true
currentVersion=4.3.7284.3916
defaultBrowser=true
emailProvider=0
enableTips=false
hiddenWindows-4_3=@Invalid()
kmlErrorHandling=0
lastHeight=743
lastLeft=1568
lastTip=2
lastTop=46
lastWidth=1024
layersOpen=true
mouseWheelSpeed=1
osName=Linux
placesOpen=true
renderWarning-OGLsoftwareEmulated=false
searchOpen=true
shown_GPS=false
shown_LeftPanel=false
shown_RenderFrame=true
shown_Ruler=false
tooltips=true
visibleWindows-4_3=RenderWindow, ServerWindow
wasFullScreen=false
wasMaximized=true

[Cache]
DiskCacheSize=2000
MemoryCacheSize=500

[Layer]
FlySpeed=0.171
drivingDirectionsRange=1000
drivingDirectionsSpeed=150
drivingDirectionsTilt=45
pauseTime=1.6
tourBalloonShow=false
tourCycles=1
tourSpeed=0.171

[Render]
AnisotropicFiltering=0
CompassVisible=true
DisableAdvancedFeatures=false
ElevationExaggeration=1
FeetMiles=true
GridReference=0
GuiFontFamily=Arial
GuiFontSize=12
GuiFontStyle=0
GuiFontWeight=50
IconSize=1
OverviewSize=34
OverviewZoom=99
PrimaryFontVersion2Family=Arial
PrimaryFontVersion2Size=12
PrimaryFontVersion2Style=0
PrimaryFontVersion2Weight=75
RenderingApi=1
SecondaryFontVersion2Family=Bitstream Vera Sans
SecondaryFontVersion2Size=12
SecondaryFontVersion2Style=0
SecondaryFontVersion2Weight=75
TerrainQuality=-1
TextureColors=1
TextureCompressionDXTC=true

[Search]
input0-4_3=assateague island

[UsageStatistics]
firstRun\day=7
firstRun\hour=11
firstRun\minute=39
firstRun\month=12
firstRun\second=34
firstRun\year=2008
loginHistory=0
numRuns=2
numRunsThisVersion=2
prevRun\day=7
prevRun\hour=11
prevRun\minute=41
prevRun\month=12
prevRun\second=55
prevRun\year=2008

[autoupdate]
InstalledVersion=4.3.7284.3916
```



ORION - It appears as if several things in your config file are missing. Compare it to mine. Are you running Google Earth 4.3? Did you install it from Synaptic?

---

### Post by acorey on 2009-09-12
This Helped me with Feisty on a HP dv2000 laptop.
Thank you!

---

### Post by aalhamer on 2009-10-06
Dear All,

I have tried every suggestion and ended up in failure, the solution to my small font problem with google earth 5 was simply to change the settings of my QT4. I know it pissed me off too.

go to your desktop
Follow to and open System> Preferences> QT 4 Settings
click on the font tab and choose the desired size. I run a 1360 resolution 18 aria was perfect.

I hope this solves the problems of many.

---

### Post by Francewhoa on 2010-03-21
Same here. Default fonts are too small in Google Earth 5. **The following worked for me.** [http://ubuntuforums.org/showthread.php?p=9004685#post9004685](http://ubuntuforums.org/showthread.php?p=9004685#post9004685)

---

### Post by martin.bartlett on 2010-08-05
I confirm - in 10.04 starting from the applications menu, GE fonts look fine, starting from a launcher created by "Add this launcher to desktop" they look awful!

How in GODS name does THAT happen??

---

### Post by AlphaLexman on 2010-09-10
I found this: [http://www.google.com/support/forum/p/earth/thread?tid=078d0b530dd9254e&hl=en]("http://www.google.com/support/forum/p/earth/thread?tid=078d0b530dd9254e&hl=en") and it fixed my problem.

---

