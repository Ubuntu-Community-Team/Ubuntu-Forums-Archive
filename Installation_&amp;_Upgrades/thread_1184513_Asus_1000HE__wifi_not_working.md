---
title: "Asus 1000HE : wifi not working"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by lucloubier on 2009-06-11
Hi !

I bought a new 1000HE eeePC that comes with XP. I installed 9.04 as dual boot and it works fine except for wifi that does not. :(

I googled for help and tried lots of things with no luck so far. I am using WPA. It works well with XP though. 

I wonder if the 9.04 is not buggy on wifi.

Anyone experience this problem ? If so, how did you fix it. I am looking for new hints to try before giving up !

Were can I download 8.10 for a test ? Does not seem to be available on Ubuntu site ...

===update===
Ubuntu 8.10 gives the same problem with wifi. Too bad!

---

### Post by Bucky Ball on 2009-06-11
Open System->Administration->Synaptics Package Manager and do a search for:
```

ubuntu-restricted-extras
```

Install. You will get a message to update. Do so. You may then be prompted to download a restricted hardware driver for your card. Give it a bit of time.

If not, try System->Admin->Hardware Drivers. What have you got in there?

---

### Post by lucloubier on 2009-06-11
Hi Bucky Ball !

I have installed this "restr..extra" and did a couple of updates. 

No hardware drivers listed (there was none before I did it). Wifi does not work either.

My wlan has a hidden name and I use WPA.

If I choose to connect a hidden network, I enter :
my wlan name 
security type (WPA & WPA2 personal)
and password 
then click connect
the little network icon starts "rolling"...
then a message box tells me required authentication

The password (shown if I click the show password box)looks like a generated pw! If I entwer my wlan pw, it goes searching for a minute and the same message appears again.

That happened before I did the "rest...extra" install.

Back to square one!

Any more clues to try ? :-(

---

### Post by synapsys on 2009-06-11
Do you have wpasupplicant installed?

If so, what wireless chipset are you using?

If you are not sure open up a terminal and give us the output of this command:

```
lspci | grep Wireless
```

Note: That's a pipe between lspci and grep not an L.

---

### Post by lucloubier on 2009-06-11
Nothing is listed.

lspci gives me 2 interesting lines though :
> 01:00.0 Network controller: RaLink RT2860
03:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)


If I do iwconfig, here is what I get :
> uc@eee-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

luc@eee-laptop:~$ 


---

### Post by lucloubier on 2009-06-12
My machine can connect to any visible wifi networks, but not on a hidden one. 

Here is what I did to overcome my problem ! 
I unchecked the "Enable Hidden Wireless" option on my wifi router and soon after I was able to connect.

This looks like a bug to me : XP machines are able to connect to a hidden network, not ubuntu ! I have lots of devices at home that were able to connect before I did that change(wii, Xbox, ipod touch, Dell laptops to name them all!).

If someone can give me how to connect to hidden wifi networks using ubuntu, I will be more than happy to try it !

---

### Post by chadk5utc on 2009-06-12
I have the Asus1000HE and had the same problems you need to get 
compat-wireless-2.6.30-rc6 and compile it I wish I could find my link to a step by step for it. Try searching the eeepc or eeebuntu forums youre sure to find a good howto
Mine works great now.
  Chad

---

### Post by chadk5utc on 2009-06-12
Hey I found it

Heres what I did to get the Wifi working:
sudo apt-get install
build-essential
linux-headers-eeepc
wicd

Then goto [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)   and get the Compat-Drivers
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)
follow directions on the site and your all set very easily done   
use iwconfig at terminal should show similar to this:  Bit Rate=54 Mb/s

Asus 1000HE 32GB SSD 2GB RAM Eeebuntu 2.0 Plus Extras 100% Working

---

### Post by lucloubier on 2009-06-14
Hi !

Maybe it works with an eeebuntu install, but apparently not on a plain 9.04 install like mine ! 

I cannot get the build-essential to install. Is it for eeebuntu install only? what repository?

By the way I checked the eeebuntu distro. I would love it (and install it) if it could make my wifi to work right away. Remember I use hidden wifi.

:(

---

