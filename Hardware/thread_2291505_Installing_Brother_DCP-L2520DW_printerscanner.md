---
title: "Installing Brother DCP-L2520DW printer/scanner"
date: 2015-08-20
forum: Hardware
---

### Post by MgFrobozz on 2015-08-20
[This was carried out on ubuntu 14.04 LTS 64-bit]

On the Amazon pages, there are multiple reports of installations being unable to connect over the network to the printer because of the Deep Sleep mode issue. I got around this in the following procedure by using a DHCP-assigned static IP address instead of the default/auto URI assigned by the installation tool.


[LIST]
[*]Turn on the printer and get its MAC address using the front-panel controls:
[LIST]
[*]Push "MENU"
[*]Use up/+ and down/- keys to select "4.Network". Push "OK"
[*]Use up/+ and down/- keys to select "7.MAC Address". Push "OK"
[*]Write down the displayed 12-digit hex number. Mine was "90489A164C9E", which corresponds to MAC address 90:48:9a:16:4c:9e, the address used below. Your address _will_ differ; add ":" after each pair of digits to get the MAC address.
[*]Push "STOP/EXIT" to leave the menu.
[/LIST]

[*]Decide on a static IP assignment. I used 192.168.100.110, the IP number used below. Your IP number will likely differ.
[*]Set up the DHCP address on ubuntu:
[LIST]
[*]Edit /etc/udhcpd.conf, and add the assignment (including the MAC address and the IP number) for the printer ...
[FONT=courier new]    # Brother DCPL2520DW laser printer
[/FONT][FONT=courier new]    [COLOR=#0000cd]static_lease 90:48:9a:16:4c:9e 192.168.100.110[/COLOR][/FONT]
[*]Edit /etc/hosts, adding an entry. I called it "brother", but you can name it otherwise ...
[COLOR=#0000cd][FONT=courier new]    # Brother DCPL2520 laser printer[/FONT]
[FONT=courier new]    192.168.100.110 brother[/FONT][/COLOR]
[*]Restart the DHCP service (in bash) ...
[COLOR=#0000cd][FONT=courier new]    sudo service udhcpd restart[/FONT][/COLOR]
[/LIST]

[*]Configure the printer to use WIFI (if desired):
[LIST]
[*]Push "MENU"
[*]Use up/+ and down/- keys to select "4.Network". Push "OK"
[*]Use up/+ and down/- keys to select "3.Setup Wizard". Push "OK"
[*]Display shows "SEARCHING SSID" ; when scanning is complete, it shows (for example) ...
[FONT=courier new][COLOR=#0000cd]SELECT up/down or OK
my_network[/COLOR]
... [/FONT]where "my_network" is the name of a wifi network (SSID). Use up/+ and down/- keys to select the network desired, then push "OK"
[*]For the prompt "Network Key" (the password), for each character in name, use up/+ and down/- keys to select the next character, then push "OK". After pushing "OK" for the last character, push "OK" once more to finish.
[*]For the prompt "Apply Settings?", push "OK"
[*]The printer will connect, then print a sheet with the network name (SSID) and mac address. It also shows other discovered networks.
[*]Push "STOP/EXIT"
[/LIST]

[*]Configure the printer to use DHCP:
[LIST]
[*]Push "MENU"
[*]Use up/+ and down/- keys to select "4.Network". Push "OK"
[*]Use up/+ and down/- keys to select "1.TCP/IP". Push "OK"
[*]Use up/+ and down/- keys to select "1.Boot Method". Push "OK"
[*]Use up/+ and down/- keys to select "DHCP". Push "OK"
[*]Use up/+ and down/- keys to select the number of DHCP retries (default is 0003)
[*]Push "STOP/EXIT"
[*]Hold down the power button until display shows ...
[FONT=courier new]    [COLOR=#0000cd]Shutting Down[/COLOR]
[/FONT]... then release the power button.
[*]Push the power button again to turn on the printer.
[*]**Note**: if you use the network menu to report the DHCP address, it will show "000.000.000.000", but it actually does have the address. To confirm that it's connected on that address, run one of the following in bash (using the name from /etc/hosts, or the IP number assigned by DHCP):
[COLOR=#0000cd][FONT=courier new]    ping brother
    ping 192.168.100.110[/FONT][/COLOR]
[/LIST]
[/LIST]

[LIST]
[*][FONT=arial]Download "Driver Install Tool" (linux-brprinter-installer-2.0.0-1.gz) from the Linux support page for Brother DCP-L2520DW ... [/FONT]
[FONT=courier new]    [http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcpl2520dw_us_eu&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcpl2520dw_us_eu&os=128)[/FONT]
Don't download the other packages, which are fetched by the installer.
[*]Unzip and run the installer (in bash) ...
[COLOR=#0000cd][FONT=courier new]    gunzip linux-brprinter-installer-2.0.0-1.gz
[/FONT][/COLOR][FONT=courier new][COLOR=#0000cd]    sudo bash linux-brprinter-installer-2.0.0-1 dcpl2520dw[/COLOR]
[FONT=arial]... with these responses:[/FONT][/FONT]
[LIST]
[*][FONT=courier new][FONT=arial]&#8203;[/FONT][/FONT]OK? [y/N] ->**y** [oks installation of lpr, cupswrapper, brscan4, and brscan-skey]
[*]Do you agree? [Y/n] ->**y** [agrees to license restrictions]
[*]Will you specify the Device URI? [Y/n] ->**y**
[*]select the number of destination Device URI. ->**10** [selects "10 (I): Specify IP address"]
[*]enter IP address ->**192.168.100.110** [uses the IP address determined above]
[*]Test Print? [y/N] ->**y** [prints out test page]
[/LIST]

[*]**Note**: when I ran the installer, it complained ...
[COLOR=#0000cd][FONT=courier new]    E: The package brscan-skey needs to be reinstalled, but I can't find an archive for it.
[/FONT][/COLOR][FONT=courier new][COLOR=#0000cd]    ERROR: No such file or directory   [/opt/brother/scanner/brscan-skey/brscan-skey-0.2.4-0.cfg][/COLOR]
[/FONT]... but this appears to affect only the scanner.
[/LIST]

[LIST]
[*]Change the printer name from "DCPL2520D" (if desired):
[LIST]
[*]Select from ubuntu menu "Applications/SystemTools/SystemSettings"
[*]Click Printers
[*]Right-click "DCPL2520D" and select "Rename"
[*]Enter the new name
[/LIST]

[*]Add support for the scanner. The port number for the scanner in this printer is 54921; the port number for other Brother printers will likely differ [anyone know why Brother does **not** use the same port number for all scanners in their product line?]
[LIST]
[*]Open the scanner port in the firewall. On my system, I used the following (your adapter may be eth0 instead):
[COLOR=#0000cd][FONT=courier new]iptables -A OUTPUT -o eth1[/FONT][FONT=courier new] -p tcp --destination-port 54921 -j ACCEPT[/FONT][/COLOR]
[*]Install the scanner, using the IP number determined above: 
[COLOR=#0000cd][FONT=courier new]brsaneconfig4 -a name="brother" model="DCP-L2520DW" ip=192.168.100.110[/FONT][/COLOR]
[*][FONT=courier new]&#8203;[/FONT]brsaneconfig4 doesn't seem to set up the sane configuration files correctly. Edit /etc/sane.d/dll.conf, and add (or uncomment) the following lines:
[COLOR=#0000cd][FONT=courier new]net
brother4[/FONT][/COLOR]
[*]Edit /etc/sane.d/brother.conf, and add the following comment and configuration line:
[COLOR=#0000cd][FONT=courier new]# Brother DCP-L2520DW:[/FONT]
[FONT=courier new]net tcp 192.168.100.110 54921[/FONT][/COLOR]
[*]Restart the sane service:
[COLOR=#0000cd][FONT=courier new]sudo service saned restart[/FONT][/COLOR]
[*]Test that your system can see the scanner by issuing this bash command:
[COLOR=#0000cd][FONT=courier new]scanimage -L[/FONT][/COLOR]
... which should report something like ...
[COLOR=#0000cd][FONT=courier new]device `brother4:net1;dev0' is a Brother brother DCP-L2520DW[/FONT][/COLOR]
[*]Verify that the scan works by loading a printed page into the scanner, then issuing this bash command: 
[COLOR=#0000cd][FONT=courier new]scanimage --device="brother4:net1;dev0" > ~/temp.pnm[/FONT][/COLOR]
[*]You can also use simple-scan. Install with bash command "apt-get simple-scan", which makes it available as simple-scan in bash, and Applications/Graphics/SimpleScan in the system menu.
[/LIST]
[/LIST]

---

### Post by SeijiSensei on 2015-08-21
I just gave my Ethernet-connected Brother printer a static IP outside the DHCP-assigned range.  Works fine.

---

