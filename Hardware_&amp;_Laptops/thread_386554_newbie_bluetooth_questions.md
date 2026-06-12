---
title: "newbie bluetooth questions"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by chrisbpr on 2007-03-17
hi,
i am an absolute beginneer so here goes.
i have just installed ubuntu on my lappy ( & very pleased with it so far), but i am having trouble seting up my usb bluetooth dongle.
i have read about using hcitool but i don't know if  i am doing this right as the new file & search systems are a bit of a mystry to be at the moment, so if anyone has a idiots guide i would be more than greatful for some help.

thanks

chris

---

### Post by kidders on 2007-03-19
Hi there and welcome,

I clicked on this thread when you posted it, and today I noticed that nobody has answered it yet! :-?

Is there something in particular that won't work right for you? What kind of things would you like to be able to do over bluetooth?

---

### Post by xnszxdotnet on 2007-03-19
this is from the book "ubunut hacks, tips and tools" hope it helps. It worked for me.

[HTML]
<html>

<META http-equiv="Content-Type" content="text/html; charset=iso-8859-1">

<head>

<title>Hack&nbsp;44.&nbsp;Make Bluetooth Connections</title>

<link rel="STYLESHEET" type="text/css" href="images/style.css">

<link rel="STYLESHEET" type="text/css" href="images/docsafari.css">

</head>

<body>

<table width="100%" border="0" cellspacing="0" cellpadding="0">

<tr><td><div STYLE="MARGIN-LEFT: 0.15in;">

<a href=I-0596527209-CHP-4-SECT-6.html><img src="images/prev.gif" width="60" height="17" border="0" align="absmiddle" alt="Previous Page"></a>

<td align="right"><div STYLE="MARGIN-LEFT: 0.15in;">

<a href=I-0596527209-CHP-4-SECT-8.html><img src="images/next.gif" width="60" height="17" border="0" align="absmiddle" alt="Next Page"></a>

</div></td></tr></table>

<br><table width="100%" border="0" cellspacing="0" cellpadding="0"><TR><td valign="top"><a name="I-0596527209-CHP-4-SECT-7"></a>

         <h3 id="title-IDASBJTF" class="docSection1Title">Hack 44. Make Bluetooth Connections</H3>

         <p class="docText">

            <img border="0" alt="" align="absmiddle" width="14" height="36" SRC="images/moderate.jpg">

            <img border="0" alt="" align="absmiddle" width="36" height="36" SRC="images/hack44.jpg">

         </p>

         <p class="docText">

            <span class="docEmphBold">Create a personal-area Bluetooth network to exchange files, send messages, and share network connections.</span>

         </p>

         <p class="docText">

            <a name="ID-ID-d1861e0-907253"></a>

            <a name="ID-ID-d1864e0-907609"></a>Bluetooth allows you to create short-range (usually 10-meter), low-bandwidth (1-2 megabits per second), ad hoc connections between devices. It's ideal for sending photos from your camera phone to your computer, or for using the wireless modem found in certain models of cell phones.</p>

         <p class="docText">To get started with Bluetooth, first make sure it's working. Some computers have built-in Bluetooth adapters. If you are using an external USB Bluetooth dongle, after you insert it you may need to run this command to reset the Bluetooth Host Controller Daemon:</p>

         <pre>$ <B>sudo killall -HUP hcid</b>

         </pre><BR>



         <p class="docText">Now, to make sure Bluetooth is really up and running, you need to make sure you have at least one device in the vicinity that is set as "discoverable" (this is a Bluetooth mode that allows devices to find one another). Check your device documentation for details on how to set discoverable mode.</p>

         <p class="docText">Some devices allow you turn on discoverable mode only for a limited time (for example, two minutes). So, make sure you execute the next command quickly. The <span class="docEmphasis">

               <a name="ID-ID-d1867e0-907293"></a>

               <a name="ID-ID-d1870e0-907611"></a>hcitool</span> utility lets you manage Bluetooth connections. Run the command <tt>hcitool</tt> 

            <tt>scan</tt> to enumerate the discoverable devices in your vicinity. Here, <span class="docEmphasis">hcitool</span> has found three devices (my Nokia 3650 cell phone, my Mac, and my Palm Treo):</p>

         <pre>bjepson@scoobuntu:~$ <b>hcitool scan</b>

Scanning ...

        00:60:57:50:AB:9C       BrianJ3650

        00:14:51:89:4D:C7       Jepstone

        00:07:E0:6A:FE:54       bjepson</pre><br>



         <a name="ID-d1705e5598-Pairing502944"></a>

            <H4 id="title-IDAJEJTF" class="docSection2Title">Pairing</h4>

            <p class="docText">

               <a name="ID-ID-d1873e0-907294"></a>Now that you know Bluetooth is working, you can <span class="docEmphasis">pair</span> your Ubuntu system with one of the devices. Pairing creates a bond between the devices so that they can exchange data and connect to one another.</P>

            <p class="docText">First, initiate pairing from the device you want to use. Each device is different. On the Treo, for example, you need to tap the Bluetooth icon and click Setup Devices<img src=images/U2192.jpg border=0>Trusted Devices<img src=images/U2192.jpg border=0>Add Device. <a class="docLink" href="#IDFigure4-11">Figure 4-11</a> shows my Palm Treo discovering several computers, including <span class="docEmphasis">scoobuntu-0</span>, my Ubuntu system. Select your Ubuntu system and tap OK. When prompted for your passkey, pick something at random. A dialog should pop up on your Ubuntu system asking for the passkey. Type the same thing into that dialog and click OK.</p>

            <a name="IDFigure4-11"></a><P><center>

               <H5 class="docFigureTitle">Figure 4-11. Palm Treo discovering nearby Bluetooth devices</H5>

               <img border="0" alt="" width="259" height="259" SRC="images/ubhk_0411.jpg">

            </center></p><br>

         

         <a name="ID-d1705e5735-ManualPairing502960"></a>

            <h4 id="title-IDASFJTF" class="docSection2Title">Manual Pairing</h4>

            <p class="docText">

               <a name="ID-ID-d1876e0-907295"></a>If that dialog doesn't appear, you will need to take matters into your own hands. Cancel the pairing procedure on your device (or wait for it to time out), and go back to your Ubuntu system. Edit <i>/etc/bluetooth/pin</i> (you need to use <span class="docEmphasis">sudo</span> to edit this, as in <tt>sudo</tt> 

               <tt>vi</tt> 

               <tt>/etc/bluetooth/pin</tt>) and change the PIN code there to the PIN you want to use as the one-time password for pairing devices (some devices allow only numeric PINs).</p>

            <p class="docText">Next, create a script called <i>/usr/local/bin/bluepincat</i> and make it executable:</p>

            <pre>#!/bin/sh

# file: /usr/local/bin/bluepincat



echo -n "PIN:" 

cat /etc/bluetooth/pin</pre><br>



            <p class="docText">Comment out the existing <tt>pin_helper</tt> line in <i>/etc/bluetooth/hcid.conf</i> (again, you need to use <span class="docEmphasis">sudo</span> to edit this file) and add the following:</p>

            <pre>pin_helper /usr/local/bin/bluepincat;</pre><BR>



            <p class="docText">Next, reset the <span class="docEmphasis">hcid</span> daemon with <tt>sudo</tt> 

               <tt>killall</tt> 

               <tt>-HUP</tt> 

               <tt>hcid</tt> and try to initiate pairing from your device again, this time using the PIN code that you put into <i>/etc/bluetooth/pin</i> as the passkey. Once you're done pairing devices, you should restore the original configuration and reset the <span class="docEmphasis">hcid</span> daemon again (this avoids the possibility of someone guessing your PIN and pairing with your computer without your knowledge or consent).</P>

         

         <a name="ID-d1705e5928-BluetoothFileTransfer502982"></a>

            <H4 id="title-IDAQHJTF" class="docSection2Title">Bluetooth File Transfer</h4>

            <p class="docText">

               <a name="ID-ID-d1879e0-907296"></a>Suppose you have something on your cell phone, such as a photo you took, that you want to send to your computer. If you install the <span class="docEmphasis">obexserver</span> package, you can receive files sent over Bluetooth:</P>

            <pre>$ <b>sudo apt-get install obexserver</b>

            </pre><br>



            <p class="docText">To receive files, you need to register the <a name="ID-ID-d1882e0-907297"></a>OBEX (Object Exchange) push service. This needs to be done each time you restart your computer (or the Bluetooth subsystem):</p>

            <pre>$ <B>sdptool add --channel=10 OPUSH</b>

OBEX Object Push service registered</pre><br>



            <p class="docText">Now, when you want to receive a file, start the obexserver and send the file from the other device. The obexserver will terminate after the transfer:</p>

            <pre>$ <B>obexserver</b>

Waiting for connection...



...............................................................

...............................................................

...............................................................

...............................................................

...................................................HEADER_LENGTH = 307254

put_done() Skipped header 05

put_done() Skipped header 42

put_done() Skipped header c0

Filename = screenshot0000.bmp

Wrote /tmp/screenshot0000.bmp (307254 bytes)



$</pre><br>



         

         <a name="ID-d1705e6162-ConnecttotheInternet503026"></a>

            <h4 id="title-IDAAJJTF" class="docSection2Title">Connect to the Internet</H4>

            <p class="docText">

               <a name="ID-ID-d1885e0-907298"></a>Many Bluetooth phones, including certain Treo models as well as many Nokia and Sony Ericsson phones, can act as a gateway between your computer and the Internet. In this configuration, the phone is commonly thought of as a "wireless modem," but in fact, the connection between your computer and the Internet is digital all the way. Still, because this configuration uses the same protocol (PPP) as most dial-up connections, it's easy and sometimes helpful to just think of it as a modem.</p>

            <p><table border="0" bgcolor="black" cellspacing="0" cellpadding="1" width="90%" align="center"><tr><td><table bgcolor="white" width="100%" border="0" cellspacing="0" cellpadding="6"><TR><TD width="60" valign="top"><img src="images/screw.jpg" width="52" height="50" alt=""></td><td valign="top">

               <p class="docText">

                  <a name="ID-ID-d1888e0-907306"></a>Before you try this, you need to contact your wireless provider to find out whether this service is supported and how much it will cost you. Some providers, such as T-Mobile in the U.S., have inexpensive flat-rate pricing of between $20 and $50 a month, depending on your level of service. But most providers will charge you <span class="docEmphasis">by the kilobyte</span> if you don't have a data plan on your account. If you're not totally clear on how much it will cost, be careful, since cellular bills of hundreds or even thousands of dollars are not unheard of, especially when you throw international roaming into the mix!</p>

            </td></TR></table></td></TR></table></p><BR>

            <p class="docText">To make the connection, you first need to set up a link between your Ubuntu system and the paired device. Edit (using <span class="docEmphasis">sudo</span>) <I>/etc/bluetooth/rfcomm.conf</I> and add an entry for your device. You'll need to specify your phone's device ID (which you can get with <tt>hciutil</tt> 

               <tt>scan</tt>, as shown earlier):</p>

            <pre>rfcomm0 {

  bind yes;

    # Bluetooth address of the device

    device <tt><i>00:07:E0:6A:FE:54</i></tt>;

    # RFCOMM channel for the connection

    channel     1;

    # Description of the connection

    comment "My Treo";

}</pre><br>



            <p class="docText">Next, edit <span class="docEmphasis">/etc/bluetooth/hcid.conf</span> (using <span class="docEmphasis">sudo</span>), scroll to the bottom, and uncomment the <tt>auth</tt> and <tt>encrypt</tt> lines so they look like this:</p>

            <pre>    # Authentication and Encryption (Security Mode 3)

    auth enable;

    encrypt enable;</pre><br>



            <p class="docText">Then, run the command <tt>sudo</tt> 

               <tt>killall</tt> 

               <tt>-HUP</tt> 

               <tt>hcid</tt> to reset the <span class="docEmphasis">hcid</span> daemon.</p>

            <p class="docText">Next, use the command <tt>sudo</tt> 

               <tt>rfcomm</tt> 

               <tt>bind</tt> 

               <tt>rfcomm0</tt> to make the connection. Now you've got a modem you can use on <i>/dev/rfcomm0</i>. Next, you need to create some PPP scripts. The first one is a <span class="docEmphasis">chat script</span>. As <span class="docEmphasis">root</span>, create <i>/etc/chatscripts/BluetoothPhone</i>. You will need to replace <tt><i>APN</i></tt> with the Access Point Name that your cellular provider uses (contact your cellular provider to get this information, or check Opera's list of APNs at <a class="docLink" target="_blank" href="http://www.opera.com/products/mobile/docs/connect/">http://www.opera.com/products/mobile/docs/connect/</a>):</p>

            <pre>TIMEOUT 10

ABORT   'BUSY'

ABORT   'NO ANSWER'

ABORT   'ERROR'

SAY     'Starting GPRS connect script\\n'



# Get the modem's attention and reset it.

""      'ATZ'



# E0=No echo, V1=English result codes

OK      'ATE0V1'



# Set Access Point Name (APN)

SAY     'Setting APN\\n'

OK  'AT+CGDCONT=1,"IP","<tt><I>APN</i></tt>"'



# Dial the number

ABORT   'NO CARRIER'

SAY     'Dialing...\\n'

OK      'ATD*99***1#'

CONNECT ''</pre><br>



            <p class="docText">The next is <I>/etc/chatscripts/BluetoothPhone-Disconnect</I>:</p>

            <pre>""      "\\K" 

""      "+++ATH0" 

SAY     "GPRS disconnected." </pre><BR>



            <p class="docText">Finally, you need a PPP peers script (<i>/etc/ppp/peers/BluetoothPhone</i>):</p>

            <pre>/dev/rfcomm0  # Bluetooth modem

115200        # speed

defaultroute  # use the cellular network for the default route

usepeerdns    # use the DNS servers from the remote network

nodetach      # keep pppd in the foreground

crtscts       # hardware flow control

lock          # lock the serial port

noauth        # don't expect the modem to authenticate itself

local         # don't use Carrier Detect or Data Terminal Ready

replacedefaultroute

debug



# Use the next two lines if you receive the dreaded messages:

#

#    No response to n echo-requests

#    Serial link appears to be disconnected.

#    Connection terminated.

#

lcp-echo-failure 4

lcp-echo-interval 65535



connect "/usr/sbin/chat -V -f /etc/chatscripts/BluetoothPhone" 

disconnect "/usr/sbin/chat -V -f /etc/chatscripts/BluetoothPhone-Disconnect"</pre><BR>



            <p class="docText">With all these scripts in place and your rfcomm device connected using <tt>rfcomm</tt> 

               <tt>bind</tt>, run the command <tt>sudo</tt> 

               <tt>pppd</tt> 

               <tt>call</tt> 

               <tt>BluetoothPhone</tt> to connect to the Internet anywhere you have cellular service. When you are done, press Ctrl-C to terminate the connection.</p>

            <p class="docText">For more information on working with cellular data connections and Bluetooth, see <span class="docEmphasis">Linux Unwired</span> by Roger Weeks et al. (O'Reilly).<a name="ID-ID-d1891e0-907254"></a>

            </p>

            <p class="docText">Brian Jepson</P>

         

      

<a href="30011536.html"><img src="images/pixel.jpg" alt="" width="1" height="1" border="0"></a></TD></TR></table>

<br>

<table width="100%" border="0" cellspacing="0" cellpadding="0">

<tr><td><div STYLE="MARGIN-LEFT: 0.15in;">

<a href=I-0596527209-CHP-4-SECT-6.html><img src="images/prev.gif" width="60" height="17" border="0" align="absmiddle" alt="Previous Page"></a>

<td align="right"><div STYLE="MARGIN-LEFT: 0.15in;">

<a href=I-0596527209-CHP-4-SECT-8.html><img src="images/next.gif" width="60" height="17" border="0" align="absmiddle" alt="Next Page"></a>

</div></td></tr></table>

</body></html>

[/HTML]

---

### Post by xnszxdotnet on 2007-03-19
sorry it should be like this...

Previous Page
	
Next Page

Hack 44. Make Bluetooth Connections

Create a personal-area Bluetooth network to exchange files, send messages, and share network connections.

Bluetooth allows you to create short-range (usually 10-meter), low-bandwidth (1-2 megabits per second), ad hoc connections between devices. It's ideal for sending photos from your camera phone to your computer, or for using the wireless modem found in certain models of cell phones.

To get started with Bluetooth, first make sure it's working. Some computers have built-in Bluetooth adapters. If you are using an external USB Bluetooth dongle, after you insert it you may need to run this command to reset the Bluetooth Host Controller Daemon:

$ sudo killall -HUP hcid
         


Now, to make sure Bluetooth is really up and running, you need to make sure you have at least one device in the vicinity that is set as "discoverable" (this is a Bluetooth mode that allows devices to find one another). Check your device documentation for details on how to set discoverable mode.

Some devices allow you turn on discoverable mode only for a limited time (for example, two minutes). So, make sure you execute the next command quickly. The hcitool utility lets you manage Bluetooth connections. Run the command hcitool scan to enumerate the discoverable devices in your vicinity. Here, hcitool has found three devices (my Nokia 3650 cell phone, my Mac, and my Palm Treo):

bjepson@scoobuntu:~$ hcitool scan
Scanning ...
        00:60:57:50:AB:9C       BrianJ3650
        00:14:51:89:4D:C7       Jepstone
        00:07:E0:6A:FE:54       bjepson


Pairing

Now that you know Bluetooth is working, you can pair your Ubuntu system with one of the devices. Pairing creates a bond between the devices so that they can exchange data and connect to one another.

First, initiate pairing from the device you want to use. Each device is different. On the Treo, for example, you need to tap the Bluetooth icon and click Setup DevicesTrusted DevicesAdd Device. Figure 4-11 shows my Palm Treo discovering several computers, including scoobuntu-0, my Ubuntu system. Select your Ubuntu system and tap OK. When prompted for your passkey, pick something at random. A dialog should pop up on your Ubuntu system asking for the passkey. Type the same thing into that dialog and click OK.

Figure 4-11. Palm Treo discovering nearby Bluetooth devices


Manual Pairing

If that dialog doesn't appear, you will need to take matters into your own hands. Cancel the pairing procedure on your device (or wait for it to time out), and go back to your Ubuntu system. Edit /etc/bluetooth/pin (you need to use sudo to edit this, as in sudo vi /etc/bluetooth/pin) and change the PIN code there to the PIN you want to use as the one-time password for pairing devices (some devices allow only numeric PINs).

Next, create a script called /usr/local/bin/bluepincat and make it executable:

#!/bin/sh
# file: /usr/local/bin/bluepincat

echo -n "PIN:" 
cat /etc/bluetooth/pin


Comment out the existing pin_helper line in /etc/bluetooth/hcid.conf (again, you need to use sudo to edit this file) and add the following:

pin_helper /usr/local/bin/bluepincat;


Next, reset the hcid daemon with sudo killall -HUP hcid and try to initiate pairing from your device again, this time using the PIN code that you put into /etc/bluetooth/pin as the passkey. Once you're done pairing devices, you should restore the original configuration and reset the hcid daemon again (this avoids the possibility of someone guessing your PIN and pairing with your computer without your knowledge or consent).
Bluetooth File Transfer

Suppose you have something on your cell phone, such as a photo you took, that you want to send to your computer. If you install the obexserver package, you can receive files sent over Bluetooth:

$ sudo apt-get install obexserver
            


To receive files, you need to register the OBEX (Object Exchange) push service. This needs to be done each time you restart your computer (or the Bluetooth subsystem):

$ sdptool add --channel=10 OPUSH
OBEX Object Push service registered


Now, when you want to receive a file, start the obexserver and send the file from the other device. The obexserver will terminate after the transfer:

$ obexserver
Waiting for connection...

...............................................................
...............................................................
...............................................................
...............................................................
...................................................HEADER_LENGTH = 307254
put_done() Skipped header 05
put_done() Skipped header 42
put_done() Skipped header c0
Filename = screenshot0000.bmp
Wrote /tmp/screenshot0000.bmp (307254 bytes)

$


Connect to the Internet

Many Bluetooth phones, including certain Treo models as well as many Nokia and Sony Ericsson phones, can act as a gateway between your computer and the Internet. In this configuration, the phone is commonly thought of as a "wireless modem," but in fact, the connection between your computer and the Internet is digital all the way. Still, because this configuration uses the same protocol (PPP) as most dial-up connections, it's easy and sometimes helpful to just think of it as a modem.

	

Before you try this, you need to contact your wireless provider to find out whether this service is supported and how much it will cost you. Some providers, such as T-Mobile in the U.S., have inexpensive flat-rate pricing of between $20 and $50 a month, depending on your level of service. But most providers will charge you by the kilobyte if you don't have a data plan on your account. If you're not totally clear on how much it will cost, be careful, since cellular bills of hundreds or even thousands of dollars are not unheard of, especially when you throw international roaming into the mix!

To make the connection, you first need to set up a link between your Ubuntu system and the paired device. Edit (using sudo) /etc/bluetooth/rfcomm.conf and add an entry for your device. You'll need to specify your phone's device ID (which you can get with hciutil scan, as shown earlier):

rfcomm0 {
  bind yes;
    # Bluetooth address of the device
    device 00:07:E0:6A:FE:54;
    # RFCOMM channel for the connection
    channel     1;
    # Description of the connection
    comment "My Treo";
}


Next, edit /etc/bluetooth/hcid.conf (using sudo), scroll to the bottom, and uncomment the auth and encrypt lines so they look like this:

    # Authentication and Encryption (Security Mode 3)
    auth enable;
    encrypt enable;


Then, run the command sudo killall -HUP hcid to reset the hcid daemon.

Next, use the command sudo rfcomm bind rfcomm0 to make the connection. Now you've got a modem you can use on /dev/rfcomm0. Next, you need to create some PPP scripts. The first one is a chat script. As root, create /etc/chatscripts/BluetoothPhone. You will need to replace APN with the Access Point Name that your cellular provider uses (contact your cellular provider to get this information, or check Opera's list of APNs at [http://www.opera.com/products/mobile/docs/connect/):](http://www.opera.com/products/mobile/docs/connect/):)

TIMEOUT 10
ABORT   'BUSY'
ABORT   'NO ANSWER'
ABORT   'ERROR'
SAY     'Starting GPRS connect script\\n'

# Get the modem's attention and reset it.
""      'ATZ'

# E0=No echo, V1=English result codes
OK      'ATE0V1'

# Set Access Point Name (APN)
SAY     'Setting APN\\n'
OK  'AT+CGDCONT=1,"IP","APN"'

# Dial the number
ABORT   'NO CARRIER'
SAY     'Dialing...\\n'
OK      'ATD*99***1#'
CONNECT ''


The next is /etc/chatscripts/BluetoothPhone-Disconnect:

""      "\\K" 
""      "+++ATH0" 
SAY     "GPRS disconnected." 


Finally, you need a PPP peers script (/etc/ppp/peers/BluetoothPhone):

/dev/rfcomm0  # Bluetooth modem
115200        # speed
defaultroute  # use the cellular network for the default route
usepeerdns    # use the DNS servers from the remote network
nodetach      # keep pppd in the foreground
crtscts       # hardware flow control
lock          # lock the serial port
noauth        # don't expect the modem to authenticate itself
local         # don't use Carrier Detect or Data Terminal Ready
replacedefaultroute
debug

# Use the next two lines if you receive the dreaded messages:
#
#    No response to n echo-requests
#    Serial link appears to be disconnected.
#    Connection terminated.
#
lcp-echo-failure 4
lcp-echo-interval 65535

connect "/usr/sbin/chat -V -f /etc/chatscripts/BluetoothPhone" 
disconnect "/usr/sbin/chat -V -f /etc/chatscripts/BluetoothPhone-Disconnect"


With all these scripts in place and your rfcomm device connected using rfcomm bind, run the command sudo pppd call BluetoothPhone to connect to the Internet anywhere you have cellular service. When you are done, press Ctrl-C to terminate the connection.

For more information on working with cellular data connections and Bluetooth, see Linux Unwired by Roger Weeks et al. (O'Reilly).

Brian Jepson

Previous Page
	
Next Page

---

### Post by Sonicgoo on 2007-04-21
After doing everything that everybody said I was jamming up still on the password. 

My phone would ask to bond with my desktop and then say that the PIN was invalid. 

Changed it to to channel 8 and it logged right in now I just need to make it permanent.

---

