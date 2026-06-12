---
title: "Music playing from Android Phone on Speakers of Ubuntu Laptop through USB."
date: 2015-09-10
forum: Hardware
---

### Post by kagashe on 2015-09-10
USB connection between my Lenovo G50-45 Laptop and Android Phone has been a challenge due to Realtek Adopter (Driver rtl8723be). I tried it by installing the drivers through ppa on Ubuntu 14.04 and 15.04. On Ubuntu 14.04.3 it works sometimes but not every time (in spite of Kernel 3.19) but now working every time on Ubuntu 15.04.

On Ubuntu 15.04 initially I could transfer files from Ubuntu Laptop to Android Phone but not from Phone to the Laptop. Then I checked "Receive files in Download folder over Bluetooth" on Personal File Sharing Preferences and I could transfer the files from Android Phone to the Laptop.

Today I was running Live Ubuntu 15.10 through Daily Live ISO (which has Linux Kernel 4.2 and built in Drivers) and I could transfer files from laptop to Android Phone but not the other way round even after checking the above option. Then I discovered that the Live ISO does not have obex server necessary for receiving files from the Android.

With the Bluetooth connection on I played mp3 music file on Android Phone which I could hear on Speakers of the laptop although it has no codecs to play mp3. While this connection was on there was padlock symbol on Bluetooth icon.

I could play the music on Ubuntu 15.04 after unchecking the file sharing options.

Kamalakar

---

