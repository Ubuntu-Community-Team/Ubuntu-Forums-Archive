---
title: "Canon Network Printer: Under Ubuntu does not print, under MINT it prints"
date: 2015-10-08
forum: Hardware
---

### Post by davidvan on 2015-10-08
Hello everyone, 

Its been too long and I need to start giving back with providing any support I can. 

Issue: I have a standard ole, Canon MPF4700n printer. Wired network, dedicated IP address.
Under Ubuntu I follow the instructions to install based on the software:

Installing on Debian Based 64 bits
1. Inside the folder "Linux_UFRII_Printerdriver_V290_us_EN" > "64-bit_Driver" > "Debian"
Right click on "cndrvcups-common_2.90-1_amd64.deb" package. Select "Open With GDebi Package Installer" option
Click on "Install Package"
When installation is finished click on "Close" button. Close the "Package Installer - cndrvups-common" window

2. Right click on "cndrvcups-ufr2-us_2.90-1_amd64.deb" package. Select "Open With GDebi Package Installer" option
Click on "Install Package"
When installation is finished click on "Close" button. Close the "Package Installer - cndrvups-ufr2-us" window
Note: To satisfy all dependencies it is important to first install cndrvcups-common_2.90-1_amd64.deb" then second install "cndrvcups-ufr2-us_2.90-1_amd64.deb".

3. If not already done power on your printer. Ensure it's connected properly to your computer.

4. Using your favourite internet browser such as*?IceWeasel go to*[http://localhost:631/admin](http://localhost:631/admin)
Click on "Add Printer" button
If the browser asks for your username and password enter your Debian Root username and password
Under "Local Printers" select the appropriate printer model
Click on "Continue" button
On the next page leave default settings as is for "Name", "Description", "Location". Unless you know what you're doing.
Click on "Continue" button
On the next page, under "Model" the appropriate printer model should be automatically selected. If not select the appropriate model.
Click on "Add Printer" button
On the next page under "General" section select your preferred settings. If unsure leave default settings.
Click on "Set Default Options"
Wait up to 30 seconds
On the next page click on "Maintenance" dropdown menu select "Print Test Page" option. Wait up to 60 seconds. If successful the printer will print a test page.

* If above is not working ensure your printer is not on hibernation or standby mode


All that said, under Ubuntu the print will never reach the printer, under Linux Mint the installation is a snap and print right off. 
Does anyone know if there is a different in HOW things print betwen Ubuntu and Mint?

Many thanks
Dave

---

