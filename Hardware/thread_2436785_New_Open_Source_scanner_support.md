---
title: "New Open Source scanner support"
date: 2020-02-13
forum: Hardware
---

### Post by markosjal on 2020-02-13
The following are s400w based scanners that can now be used with SANE. They all look identical except for color and branding.
[IMG]https://user-images.githubusercontent.com/281916/74772185-24200f00-5255-11ea-9c2d-ad39bea7a418.jpg[/IMG]
[IMG]https://user-images.githubusercontent.com/281916/74772187-24b8a580-5255-11ea-8690-95ec6240e691.jpg[/IMG]
[LIST]
[*]Century CPS-A4WF
[*]Halo Magic Scanner
[*]ION AirCopy
[*]ION AirCopy E-Post Edition
[*]iScan Fly
[*]Kaiser Baas WiFi Photo & Document Scanner
[*]Mustek iScan Air / S400W
[*]Transcription Patri Kun A4 Wi-Fi Portable Scanner
[*]&#36578;&#20889;&#12497;&#12483;&#12488;&#12522;&#12367;&#12435; A4 Wi-Fi&#12509;&#12540;&#12479;&#12502;&#12523;&#12473;&#12461;&#12515;&#12490;&#12540;
[/LIST]


SANE support for these scanners is a 2 part process 

Install first 
[https://github.com/markosjal/AirScan](https://github.com/markosjal/AirScan)
This runs on Apache2 and php 7.0 fully tested and developed on Ubuntu 16.04.  This can be installed to a network host machine or a local machine, as long as it has a wireless connection dedicated to the scanner in addition to your LAN connection. It can even be installed to a Raspberry Pi 2 or 3. Then use the Web GUI to test scanning. Now that you have installed AirScan you should have eSCL Scanning support for you s400w based scanner.

Install second
sane-airscan [https://github.com/alexpevzner/sane-airscan](https://github.com/alexpevzner/sane-airscan)
This package is used to connect to eSCL scanners, or in our case to the AirScan software we just installed. I believe there is an Ubuntu repo there too. [IMG]https://user-images.githubusercontent.com/281916/74394074-6d91d980-4dd1-11ea-8620-19d46b07c947.png[/IMG]
[https://user-images.githubusercontent.com/281916/74394077-708cca00-4dd1-11ea-80ca-89f343bc9210.png](https://user-images.githubusercontent.com/281916/74394077-708cca00-4dd1-11ea-80ca-89f343bc9210.png)

For Windows, and OSX users they can now use VueScan (a separate commercial product) to access the same scanner over the network, as once AirScan is installed, it will auto-detect as eSCL scanner in VueScan. Mac Users note that we still have  compatibility issue with OSX apps scanning directly, but VueScan does work.

---

### Post by mastablasta on 2020-02-14
though these names all sound a bit exotic to me, thank you for providing the support for them.

---

### Post by markosjal on 2020-02-15
mastablasta ?? A reference to Arrow?

---

