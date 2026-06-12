---
title: "printer canon i-sensys MF 4120"
date: 2016-03-16
forum: Hardware
---

### Post by telegiovi on 2016-03-16
I just installed Ubuntu 15.10 (as in all pc's in our home), but I am not able to have the printer working. If I clic on "features" (in italian is "proprietà") I see that there is written "inactive" although is habilitated.
I fear I did not install drivers properly. But do not know how to go on now. Thank you for a help.

---

### Post by Edison_James on 2016-03-17
> **telegiovi said:**
> I just installed Ubuntu 15.10 (as in all pc's in our home), but I am not able to have the printer working. If I clic on "features" (in italian is "proprietà") I see that there is written "inactive" although is habilitated.
I fear I did not install drivers properly. But do not know how to go on now. Thank you for a help.

Did you try this?
[http://ubuntuportal.com/2011/12/how-to-install-canon-printer-driver-for-linux-ubuntu.html](http://ubuntuportal.com/2011/12/how-to-install-canon-printer-driver-for-linux-ubuntu.html)

---

### Post by seanos on 2016-03-18
> **Edison_James said:**
> Did you try this?
[http://ubuntuportal.com/2011/12/how-to-install-canon-printer-driver-for-linux-ubuntu.html](http://ubuntuportal.com/2011/12/how-to-install-canon-printer-driver-for-linux-ubuntu.html)

The repository mentioned on that page is very out of date - don’t use it!

Canon supplies printer drivers (I just installed a Pixma MG7560 today) so that’s the obvious place to start. Choose the one for your version of Ubuntu (Linux 32-bit or 64-bit).

[Canon i-SENSYS MF4120 Drivers]("http://www.canon-europe.com/support/consumer_products/products/fax__multifunctionals/laser/laserbase_mf_series/i-sensys_mf4120.aspx?type=drivers&language=IT")

Now if only I could get my scanner to work!

---

### Post by telegiovi on 2016-03-18
Yes I did download the drivers from Canon web site

---

### Post by seanos on 2016-03-18
But it’s not working?

I downloaded their HTML manual and followed these instructions. The name of the file you downloaded (& the directory) might be different for you. If you follow the first couple of commands the prompts it gives you should be easy enough to follow without reading all this!
[HR][/HR]
[LIST=1]
[*]**Install the printer driver**
Install the printer driver by entering the following command from the command line of a terminal software.

…

[B]For Ubuntu 14.04
[/B](1) Expanding the archived file and switching to the expanded directory
```
[user@zzz /yyy]$ [COLOR=#008080]tar zxvf cnijfilter2-5.00-x-deb.tar.gz[/COLOR]
[user@zzz /yyy]$ [COLOR=#008080]cd cnijfilter2-5.00-x-deb[/COLOR]
```
(2) Installing the printer driver
```
 [user@zzz /yyy]$ [COLOR=#008080]sudo ./install.sh[/COLOR]
```

When the installation is completed, a message instructing you to register the printer is displayed.
```
Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
>
```
Check that the machine is properly connected and that the power is on. Then press the Enter key.
&#8194; 
[*]**Select the connection method**
 Select the connection method for this machine.
Select the connection method to be used, and then press Enter.
```
1) USB

 2) Network
Select the connection method.[1]
```
For a USB connection, enter "1" and press the Enter key.
For a network connection, enter "2" and press the Enter key.

The default selection value is displayed in [ ].
&#8194; 
[*]**Select the printer**
From the list of detected printers, select the printer to be registered.

• Example when the model is not network enabled or when USB is selected in "2. Select the connection method"
```
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
----------------------------------------------------------
0) Update
----------------------------------------------------------
Target printers detected
1) Canon MB5300 series (//Canon/?port=usb&serial=200123)
----------------------------------------------------------
Currently selected:[1] Canon MB5300 series (//Canon/?port=usb&serial=200123)
Enter the value.[1]
```

&#9998; When connection of non-target printer model is confirmed, "Other printers detected" is displayed.

Enter the number of the printer to be registered, and then press Enter.
  To update the list of detected printers, enter "0" and press the Enter key.
To end the installation without registering the printer, enter "Q" and press the Enter key.

• Example when Network is selected in "2. Select the connection method"
```
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
----------------------------------------------------------
0) Update
----------------------------------------------------------
Target printers detected (MAC address  IP address)
1) Canon MB5300 series (XX-XX-XX-XX-XX-XX YYY.YYY.YYY.YYY)
2) Canon MB5300 series (XX-XX-XX-XX-XX-XX YYY.YYY.YYY.YYY)
----------------------------------------------------------
Currently selected:[1] Canon MB5300 series (XX-XX-XX-XX-XX-XX YYY.YYY.YYY.YYY)
Enter the value.[1]
```
In an actual message, "XX-XX-XX-XX-XX-XX" shown in the above example   displays the MAC address and "YYY.YYY.YYY.YYY" displays the IP address.

If the network contains more than one printer of the target model, the message lists multiple "Target printers detected."
In this case, check the MAC address and IP address from the Operation  Panel, and select the number of the printer matching the displayed  network address.

&#9998; When connection of non-target printer model is confirmed, "Other printers detected" is displayed.

Enter the number of the printer to be registered, and then press Enter.

To update the list of detected printers, enter "0" and press the Enter key.
To end the installation without registering the printer, enter "Q" and press the Enter key.

 &#9998; For information about checking the MAC address and IP address of the machine, refer to the "[Online Manual.]("http://rs.ciggws.net/rd2.cgi?FNC=LNX_HELP&OSV=W&LNG=EN&CTN=TOP%2FTop.html")"

&#9919; If the printer registration procedure was terminated before completion or if you canceled processing by entering "Q," use the lpadmin  command to register the printer. For instructions, refer to "Installing  the printer driver by specifying the package," and start from "3. Restarting the CUPS daemon."
&#9919; If the model is network enabled, you must re-register the printer if you  switch the wired/wireless status of the machine, because the wired LAN  and the wireless LAN have different MAC addresses.
&#8194; 
[*]**Enter the registered printer name**
Enter the registered printer name.
You can specify the desired name as the registered printer name.
```
Enter the printer name.[MB5300USB]
```
Enter the registered printer name, and press the Enter key.
If the entered printer registration name is already registered, a  message confirming whether you want to overwrite the existing  information is displayed.
```
The printer name you entered already exists. Do you want to overwrite it?
Enter [y] for Yes or [n] for No. [y]
```
&#8194; 
[*]**Set the default printer**
Set the default printer to be used when the printer name is omitted in the print command.
```
Do you want to set this printer as the default printer?
Enter [y] for Yes or [n] for No. [y]
```
&#8194; 
[*]**Installation complete**
When the installation is completed, the name registered for the installed printer is displayed.
During printing, be sure to specify the printer name displayed here.

Example when "MB5300USB" is registered as the printer name:
```
 Installation has been completed.
Printer Name : MB5300USB
Select this printer name for printing.
``` 
[/LIST]
[HR][/HR]

---

