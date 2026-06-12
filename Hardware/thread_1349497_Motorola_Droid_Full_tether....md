---
title: "Motorola Droid Full tether..."
date: 2009-12-08
forum: Hardware
---

### Post by modmadmike on 2009-12-08
Is there any way other than Proxiod to Tether my unrooted Motorola DROID. Proxiod works but I need more than just port 80.

---

### Post by aysiu on 2009-12-09
Root it?

---

### Post by modmadmike on 2009-12-09
> **aysiu said:**
> Root it?

Cant do it till it is known how to lol I wish. :p

---

### Post by aysiu on 2009-12-10
> **modmadmike said:**
> Cant do it till it is known how to lol I wish. :p
I think your wish came true:
[http://www.redmondpie.com/root-motorola-droid-on-android-2.0.1-9140198/](http://www.redmondpie.com/root-motorola-droid-on-android-2.0.1-9140198/)

---

### Post by Neezer on 2009-12-10
Does this mean you can use your droid like an aircard w/o having to buy one and pay the extra fees for it?

EDIT: I'm looking into getting a droid and the fact that I might be able to get rid of the charge for my aircard is a huge plus....I would have no idea how to set it up once it was "unlocked" as the tutorial says.

---

### Post by aysiu on 2009-12-10
> **Neezer said:**
> Does this mean you can use your droid like an aircard w/o having to buy one and pay the extra fees for it?

EDIT: I'm looking into getting a droid and the fact that I might be able to get rid of the charge for my aircard is a huge plus....I would have no idea how to set it up once it was "unlocked" as the tutorial says.
As long as your droid has an unlimited data plan, then you shouldn't need an AirCard if you've rooted it.

There is wireless tethering and also USB tethering.

---

### Post by paulisdead on 2009-12-10
I feel like I should warn you guys and say, on my G1, network manager has never worked with the wifi tethering, and Ubuntu is noted on their site as having terrible ad-hoc support.

USB tethering with the Cyanogen firmware has worked really well, and doesn't completely kill the battery.  I just make sure USB debugging mode is enabled, and whenever I plug it into an ubuntu box, it detects it and works right away, no configuration required.  I don't think Cyanogen runs on the droid, yet, but there maybe an individual package for it you can install on a rooted phone.

Also, if you're not running a custom firmware that includes it, you need to update the kernel so you have the iptables modules to enable tethering of any sort.  So this definitely requires root.  I could be wrong on this, too though, since iirc the droid runs a newer version of android than what's available on any other handset right now, so maybe it has a kernel that'll work.

---

### Post by Shannon_VanWagner on 2009-12-31
Here's the instructions for the HTC Magic:
[http://ubuntuforums.org/showpost.php?p=7446857&postcount=8](http://ubuntuforums.org/showpost.php?p=7446857&postcount=8)

---

### Post by Shannon_VanWagner on 2009-12-31
From my blog entry [here]("http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html").

So if you're like me you recently picked up the fabulous Verizon Droid Linux-based phone, and now you're one happy camper.

I've been cruising along with my Droid for a month now, and I'm happy as a clam. I have to tell you... The Verizon Droid is quite a fine Linux-based device indeed.

So now that I've used the Droid for awhile, I set out in search of a piece of functionality that I hadn't yet replaced from my Blackberry days. That is: The capability to tether my Droid as an Internet modem to my Ubuntu GNU/Linux 9.10 machine using the USB cable.

On the Blackberry, this was as simple as, a.) provisioning the data service through Verizon(yes, this does cost extra), and then b.) setting up the "Berry4All/BBTether" script (by the extravagant Mr. [Thibaut Colar]("http://wiki.colar.net/home")) on my Ubuntu Linux box.

In my search for a solution, the first place I checked for a tethering application was in the Android Market. And while there are many other applications, the only app I was able to find for tethering, required for my phone to be "rooted". And so instead of jumping right into that, I went looking for an easier solution, and voila! - I found it.

What I found is some easy tethering instructions by the masterful [Shwan.c]("http://ubuntuforums.org/member.php?u=624954") on [this post]("http://ubuntuforums.org/showpost.php?p=7446857&postcount=8") at [Ubuntuforums.org]("http://ubuntuforums.org/"). So now there was only one problem: I'm using the Verizon Droid, not the HTC Magic. The good news is that the process is generally the same, except for a difference in hardware id information for the udev rules settings in Ubuntu.

So after some minor changes, I've now successfully tethered my Verizon Droid via USB as a modem for my Ubuntu GNU/Linux 9.10 machine.

So here are the easy steps to get you up and running with using your Droid as a USB tethered modem (and a big Thanks to Shwan.c for posting the original idea):

1.) Download the current Android SDK (Linux version) from:[http://developer.android.com/sdk/download.html?v=android-sdk_r04-linux_86.tgz](http://developer.android.com/sdk/download.html?v=android-sdk_r04-linux_86.tgz)

2.) Extract the SDK, then navigate to the folder where the adb application is:

tar xvf android-sdk_r04-linux_86.tgz
cd android-sdk-linux_86/tools

3.) Copy the "adb" application to your Ubuntu /usr/bin directory (sudo privs needed)

sudo cp adb /usr/bin/adb

4.) Create/edit/save a rules file for udev to allow your machine to see your device

sudo vi /etc/udev/rules.d/91-android.rules

Put the text below into the file(using "i" to enter "insert" mode and hitting the escape key to return to "select" mode before saving.. C'mon, what fun would Linux be without using vi? If you really don't like vi, you can substitute with something like gedit, or nano, or kate, or etc.), replace USERNAME with your Linux username, then type ZZ to save the file from vi.

SUBSYSTEM=="usb", ATTRS{idVendor}=="22b8", SYMLINK+="android_adb", MODE="0666", OWNER="USERNAME"

5.) Set the appropriate permissions to the rules file you just created.

sudo chmod a+r /etc/udev/rules.d/91-android.rules

6.) Restart udev to load the new rule.

sudo restart udev

7.) Enable "USB debugging" on your Verizon Droid via Settings>Applications>Development

8.) Connect your Droid to the computer with the USB cable and then use the following adb command to check for your device.

adb devices

example:
$ adb devices
List of devices attached
040364FA0901E011

9.) Install openvpn on Ubuntu so you can connect to your device with it.

sudo apt-get install network-manager-openvpn openvpn
sudo /etc/init.d/networking restart
sudo /etc/init.d/NetworkManager restart

10.) Install openvpn on your Verizon Droid.

cd /home/Downloads/
mkdir azilink
cd azilink
wget [http://lfx.org/azilink/azilink.apk](http://lfx.org/azilink/azilink.apk)
adb install azilink.apk
wget [http://azilink.googlecode.com/files/azilink.ovpn](http://azilink.googlecode.com/files/azilink.ovpn)

11.) Create a replacement resolv.conf file to be copied over to your /etc directory at run-time:

vi resolv.conf

#Type in the text below(hit "i" for insert first, then ESC after the insert, before saving) and then hit ZZ to save

domain lan
search lan
nameserver 192.168.56.1

12.) Now create a very small script to start the modem

vi start_modem

#Type in the text below, then hit ZZ to save
adb forward tcp:41927 tcp:41927
sudo cp resolv.conf /etc/
sudo openvpn --config azilink.ovpn

13.) Set your new script to be executable.

chmod 755 start_modem

14.) On your Verizon Droid, launch the azilink app and place a checkmark by "Service active" so it can receive the connection from your Ubuntu machine.

15.) With your wireless connection in Ubuntu "unchecked"(via right-click of the Network manager applet), launch the the connection script you just made in the Terminal:

/home/Downloads/azilink/start_modem

You should now be able to surf the Internet, using your Verizon Droid as a tethered modem. When you're finished - hit ctrl+c at the Terminal from which you started the connection script. Then uncheck "Service active" on your Droid.

Cheers!

---

### Post by YQ002lc2 on 2009-12-31
Great!!!  Thanks to Shannon_VanWagner for posting such good instructions!!!! I was able to set it up on my droid without any problems. 

Now, I have another question. It works, but I get all sorts of error messages saying that the connection is unencrypted and that everything will be sent as plain text.Obviously, that is not good. 

Is there a way to encrypt the connections so that passwords and all will be secured?

---

### Post by Shannon_VanWagner on 2009-12-31
I've noticed the "unsecured vpn" messages you noted as well... but unless I'm mistaken, which is unbelievably and entirely possible, I think it only means that the connection between your machine and the Droid-phone, using the USB cable (as opposed to wireless) is what's not being encrypted by the vpn, which doesn't really seem necessary anyway. The way I see it, the Droid being tethered via the USB cable is meant to be more of a web-traffic forwarding device than it is a traffic-encrypting device.

So if you go to https://blahblah - you still get the encryption via your SSL connection witht that website... but if you FTP to someplace, than your FTP password is in cleartext just as it always is anyway.

So this doesn't seem like it would be a big deal because it wouldn't be any more dangerous than putting your Droid-phone on an internal wired Ethernet network with your Ubuntu machine anyway.

Is there a different explanation that I'm not taking into account here?

---

### Post by darkknight045 on 2010-01-17
I followed the steps, when I run the script my phone acknowledges that it has connected to the host, but my computer won't actually use the connection.  Its as if my computer does not acknowledge the connection is available (ie. zero traffic going through my phone).

---

### Post by GoodPanos on 2010-01-28
Any way to get Azilink to work via Bluetooth?

---

### Post by RustyWyatt on 2010-03-01
Howdy,

I am very new to this even though I have used Unbuntu for a number of years...

I have tried to follow these instructions faithfully.

After I cmod I try to run the "start_modem" and I get the following:

tcd@tcd-laptop:~/azilink$ chmod 755 start_modem

tcd@tcd-laptop:~/azilink$ dir
azilink.apk  azilink.ovpn  resolv.conf	start_modem
tcd@tcd-laptop:~/azilink$ start_modem
start_modem: command not found
tcd@tcd-laptop:~/azilink$ 

I have gone through the installation a couple of times so I get a few "already installed" msg's.  However, this is a clean install of 9.10.

All help GREATLY appreciated!

Thanks,
Tom

---

### Post by Shannon_VanWagner on 2010-03-01
@RustyWyatt, from the looks of your output it appears that you are not prefixing the command with './'

So instead of
~/azilink$ start_modem

Try
~/azilink$./start_modem

Cheers!

---

### Post by MCVenom on 2010-03-01
Don't know what to say, I was able to tether my Droid to Linux Mint without much problem (auto-detected, connected using network-manager) ^^;

Am I just lucky? (Sorry to hijack thread ^^; )

---

### Post by RustyWyatt on 2010-03-01
Howdy Shannon,

Thanks Very Much for the quick reply!

My frustration is that I just don't know enough about simple Linux navigation and basic functions... ;-(

Anyway...  I checked everything over and found a mistake and it now runs Great!

Thanks for your support and assistance!

Tom

---

### Post by PanamaJack on 2010-11-08
Great post! Super appreciate the help. Worked great. Couple of side notes. On Android when you download openvpn, it shows the market place app as (root). My phone is not rooted. 

Thanks again!

---

### Post by Shannon_VanWagner on 2010-11-08
> **PanamaJack said:**
> Great post! Super appreciate the help. Worked great. Couple of side notes. On Android when you download openvpn, it shows the market place app as (root). My phone is not rooted.

@PanamaJack - It sounds like you are trying to download openvpn on your Android phone? If so, this is not necessary. OpenVPN gets installed on the computer that will use it to tether with the Android phone. Azilink is the only thing that gets installed on the phone.

---

### Post by Geremia on 2010-12-25
> **darkknight045 said:**
> I followed the steps, when I run the script my phone acknowledges that it has connected to the host, but my computer won't actually use the connection.  Its as if my computer does not acknowledge the connection is available (ie. zero traffic going through my phone).Yes, I have the same problem, too. ```
ifconfig
``` shows the tun0 interface, but the network manager doesn't nor does it allow me to create it or connect to it.

---

