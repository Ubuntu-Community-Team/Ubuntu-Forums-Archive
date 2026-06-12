---
title: "UE Boom 2 unable to pair over bluetooth"
date: 2016-10-25
forum: Hardware
---

### Post by nixoninof on 2016-10-25
Hi, I have this UE Boom 2 for over a month now. It used to work nice with my lenovo-l540 laptop at the beginning, but a few weeks ago I updated the speaker over my phone, and it doesn't pair with my laptop ever since. It works just as fine with my phone. It's getting frustrated as I crawl through internet for a solution but unable to find one.

I am running XUbuntu 16.04.1 LTS on my laptop, and use blueman as the bluetooth manager. 

Sorry if I am ignoring some important detail. I am not very experienced with this kind of problems.

Thanks anyone who has an answer :(

---

### Post by jeremy31 on 2016-10-25
It doesn't pair or doesn't connect?  There are a few bugs with bluetooth audio in 16.04/16.10 but I haven't heard of a pairing issue.  If blueman lists the Boom 2 in the device list, delete it and then in terminal run ```
bluetoothctl
``` put the speaker in pairing mode and then scan with blueman to see if you can pair with it, then trust and post the output from terminal, use CTRL + d to quit bluetooth ctl

---

### Post by nixoninof on 2016-10-25
```
[NEW] Controller 10:4A:7D:FE:53:5C *****-ThinkPad-L540 [default]
[NEW] Device 88:C6:26:81:D7:CA UE BOOM 2
[CHG] Device 88:C6:26:81:D7:CA UUIDs: 000061fe-0000-1000-8000-00805f9b34fb
[CHG] Controller 10:4A:7D:FE:53:5C Discovering: yes
[NEW] Device 6D:13:78:DB:0A:22 6D-13-78-DB-0A-22
[CHG] Device 88:C6:26:81:D7:CA Connected: no
[CHG] Device 88:C6:26:81:D7:CA RSSI: -48
[CHG] Device 88:C6:26:81:D7:CA Connected: yes
[CHG] Device 88:C6:26:81:D7:CA RSSI is nil
[CHG] Device 6D:13:78:DB:0A:22 RSSI is nil
[CHG] Controller 10:4A:7D:FE:53:5C Discovering: no
[CHG] Device 88:C6:26:81:D7:CA Paired: yes
[CHG] Device 88:C6:26:81:D7:CA Connected: no
[CHG] Device 88:C6:26:81:D7:CA Connected: yes
[CHG] Device 88:C6:26:81:D7:CA Trusted: yes
[CHG] Device 88:C6:26:81:D7:CA Connected: no
[CHG] Device 88:C6:26:81:D7:CA Connected: yes
[UE BOOM 2]# quit
[DEL] Controller 10:4A:7D:FE:53:5C

```
this is the output to the run. i get the "congratulations, device successfully added" message, but afterwards i can't use the boombox as an audio sink (or anything for that matter), and the boombox itself doesn't give any indication that a device connected to it (normally it plays a subtle percussion to notify you).

---

### Post by jeremy31 on 2016-10-25
I would try this
```
sudo add-apt-repository ppa:themuso/ppa
sudo apt-get update && sudo apt-get upgrade
```

Reboot and check ```
pactl list short | grep bluetooth
```

Hopefully you see
```
module-bluetooth-policy		
module-bluetooth-discover
```

Listed in the results, if one is missing you can load it with
```
pact load-module module-name
```

Replacing module-name with the missing module.  Then try to pair again and connect.  The PPA belongs to Luke Yelavich who is working on some of the new pulseaudio/bluez issues.  Here is one bug about connecting issue [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1574324)

---

### Post by nixoninof on 2016-10-25
Unfortunately either of these modules are running after doing the steps. More unfortunate is, when i try to load them I get this

```
***@***-ThinkPad-L540:~$ pactl load-module module-bluetooth-discover
Failure: Module initialization failed
***@***-ThinkPad-L540:~$ pactl load-module module-bluetooth-policy
Failure: Module initialization failed

```

Tried to google the problem, but my frustration persists :/

---

### Post by jeremy31 on 2016-10-25
Try ```
sudo apt-get install pulseaudio-module-bluetooth
```
Reboot and you should be able to load them

---

### Post by nixoninof on 2016-10-26
Yes now both of these modules are running. But again the connection problem continues. This time it solely says "Failed to add device".

I did the bluetoothctl run again.

```
***@***-ThinkPad-L540:~$ bluetoothctl [NEW] Controller 10:4A:7D:FE:53:5C ***-ThinkPad-L540 [default]
[CHG] Controller 10:4A:7D:FE:53:5C Discovering: yes
[NEW] Device 88:C6:26:81:D7:CA UE BOOM 2
[CHG] Device 88:C6:26:81:D7:CA RSSI is nil
[CHG] Controller 10:4A:7D:FE:53:5C Discovering: no
[CHG] Device 88:C6:26:81:D7:CA Connected: yes
[CHG] Device 88:C6:26:81:D7:CA UUIDs: 000061fe-0000-1000-8000-00805f9b34fb
[CHG] Device 88:C6:26:81:D7:CA Connected: no
[bluetooth]# quit



```

---

### Post by jeremy31 on 2016-10-26
Try doing ```
bluetoothctl
```

Then wait for it to say Connected:no
then ```
connect 88:C6:26:81:D7:CA
```
See if it works

---

### Post by nixoninof on 2016-10-28
This is what happens when i try to manually connect.
```
[UE BOOM 2]# connect 88:C6:26:81:D7:CAAttempting to connect to 88:C6:26:81:D7:CA
Failed to connect: org.bluez.Error.NotAvailable
```

On the other hand, pairing supposedly works. But no reaction from the boombox itself. Also it's not listed as an audio output or anything.
```
# pair 88:C6:26:81:D7:CAAttempting to pair with 88:C6:26:81:D7:CA
Pairing successful

```

This is the info about the device.
```
[UE BOOM 2]# info 88:C6:26:81:D7:CADevice 88:C6:26:81:D7:CA
    Name: UE BOOM 2
    Alias: UE BOOM 2
    Class: 0x240418
    Icon: audio-card
    Paired: yes
    Trusted: no
    Blocked: no
    Connected: yes
    LegacyPairing: no
    UUID: Serial Port               (00001101-0000-1000-8000-00805f9b34fb)
    UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
    UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: Handsfree                 (0000111e-0000-1000-8000-00805f9b34fb)
    UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
    UUID: Unknown                   (000061fe-0000-1000-8000-00805f9b34fb)
    Modalias: bluetooth:v000ApFFFFdFFFF

```

And a weird thing; this keeps randomly happening every 15 seconds or so. It just disconnects and connects in a few seconds. Again, no reaction from the boombox itself that something connects or disconnects..
```
[CHG] Device 88:C6:26:81:D7:CA Connected: no[CHG] Device 88:C6:26:81:D7:CA Connected: yes
[CHG] Device 88:C6:26:81:D7:CA Connected: no
[CHG] Device 88:C6:26:81:D7:CA Connected: yes
[CHG] Device 88:C6:26:81:D7:CA Connected: no
[CHG] Device 88:C6:26:81:D7:CA Connected: yes

```

---

### Post by jeremy31 on 2016-11-01
Try this as it usually works for me ```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect 88:C6:26:81:D7:CA\n quit"|bluetoothctl;sleep 5; echo -e "connect 88:C6:26:81:D7:CA\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
```

---

### Post by nixoninof on 2016-11-05
OMG It's working!! Thanks a lot.. I was completely hopeless to be honest.

---

### Post by physe on 2016-11-06
> **jeremy31 said:**
> Try this as it usually works for me ```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect 88:C6:26:81:D7:CA\n quit"|bluetoothctl;sleep 5; echo -e "connect 88:C6:26:81:D7:CA\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
```

Hi,

I have exactly the same problem - my UE BOOM 2 stopped pairing to my pc (while it used to pair and work nicely).
It could be either the firmware upgrade I ran through my mobile, or some recent Ubuntu upgrade.

The above command fails for me, and I suspect the reason is that this part:

  pacmd list-cards | grep bluez_card

returns nothing...

Any suggestion?
Thanks!

---

### Post by zair.abdel on 2017-01-19
Hi guys, 
I hava the same issue, and the command info return this :
[UE BOOM 2]# info 88:C6:26:C5:42:F5
Device 88:C6:26:C5:42:F5
	Name: UE BOOM 2
	Alias: UE BOOM 2
	Paired: yes
	Trusted: yes
	Blocked: no
	Connected: yes
	LegacyPairing: no
	UUID: Unknown                   (000061fe-0000-1000-8000-00805f9b34fb)
[CHG] Device 88:C6:26:C5:42:F5 Connected: no

can someone save us!
Thanks a lot 
ps: i'm a novice but i understand quickly.

---

### Post by Planetouched on 2017-02-15
Hello everyone,
I'm afraid I'm stuck with the same kind of problem: my UE Boom 2 connect, are paired, but are not recognized by the sound setting and I can't send any sound through.
I've tried installing blueman, but when right-clicking on my loudspeaker, no options are shown for "audio profile".
I've done everything jeremy31 told to do, with no success. I'm using Ubuntu 16.04 on a Dell XPS 13.
Here is the output of the script:

```
XXXX@XXXX:~$ pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect 88:C6:26:EA:1D:1E\n quit"|bluetoothctl;sleep 5; echo -e "connect 88:C6:26:EA:1D:1E\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
You need to specify a profile by its name.
[NEW] Controller 9C:B6:D0:D3:FF:0E XXXX [default]
[NEW] Device 88:C6:26:EA:1D:1E UE BOOM 2
[bluetooth]# disconnect 88:C6:26:EA:1D:1E
Attempting to disconnect from 88:C6:26:EA:1D:1E
[bluetooth]#  quit
[DEL] Controller 9C:B6:D0:D3:FF:0E XXXX [default]
[NEW] Controller 9C:B6:D0:D3:FF:0E XXXX [default]
[NEW] Device 88:C6:26:EA:1D:1E UE BOOM 2
[bluetooth]# connect 88:C6:26:EA:1D:1E
Attempting to connect to 88:C6:26:EA:1D:1E
[bluetooth]#  quit
[DEL] Controller 9C:B6:D0:D3:FF:0E XXXX [default]
You need to specify a profile by its name.
```


Any help will be greaty appreciated!

---

### Post by jeremy31 on 2017-02-18
Does module-bluetooth-discover show in results for ```
pactl list short | grep blue
```

---

### Post by Planetouched on 2017-02-19
Yes jeremy31, it does, along with module-bluetooth-policy and module-bluez5-discover.

---

### Post by Planetouched on 2017-02-25
Anything else I could try?

---

### Post by jeremy31 on 2017-02-25
After right clicking on the device in Blueman does it give the option to connect to Audio Sink?

---

### Post by Planetouched on 2017-02-25
Well, "Audio sink" does appear in the menu when right-clicking, but it crashes when I click on it:

blueman-manager crashed with dbus.exceptions.DBusException in call_blocking():org.freedesktop.DBus.Error.LimitsExceeded: Connection"1.105" is not allowed to add more match rules (increase limits in configuration file if required)

---

### Post by jeremy31 on 2017-02-25
Does it also show headset or handsfree?

---

### Post by Planetouched on 2017-02-27
No, it only shows my UE Boom 2. It is my only bluetooth device. Strange indeed!

---

### Post by jeremy31 on 2017-02-27
I meant does it give the option to connect to headset or handsfree when right clicking on the UE Boom 2 in Blueman

Have you installed updates since installing Ubuntu, there should have been an update for Pulseaudio that included a fix for some issues with Pulseaudio crashing when connecting to a bluetooth headset

---

### Post by Planetouched on 2017-02-27
Thanks again for your help, jeremy31.
This is not clear to me: the options "headset" and "handsfree" do appear in the menu, along with "audio sink", but under "disconnect" and not "connect to".
I've let my Ubuntu 16.04 LTS update when needed, and I believe my software is up-to-date.
Synaptic tells me that my version of pulseaudio is 1:8.0-0ubuntu3.2

---

### Post by jeremy31 on 2017-02-27
Please post results for ```
pacmd list-cards
```

---

### Post by Planetouched on 2017-02-28
Here they are. Thanks!

```
1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1f.3>
    driver: <module-alsa-card.c>
    owner module: 6
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xdc428000 irq 130"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9d71"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Analog Stereo Input (priority 60, available: unknown)
        output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
        output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400, available: unknown)
        output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analog Stereo Input (priority 5460, available: unknown)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300, available: unknown)
        output:hdmi-surround+input:analog-stereo: Digital Surround 5.1 (HDMI) Output + Analog Stereo Input (priority 360, available: unknown)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 300, available: unknown)
        output:hdmi-surround71+input:analog-stereo: Digital Surround 7.1 (HDMI) Output + Analog Stereo Input (priority 360, available: unknown)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5200, available: unknown)
        output:hdmi-stereo-extra1+input:analog-stereo: Digital Stereo (HDMI 2) Output + Analog Stereo Input (priority 5260, available: unknown)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 100, available: unknown)
        output:hdmi-surround-extra1+input:analog-stereo: Digital Surround 5.1 (HDMI 2) Output + Analog Stereo Input (priority 160, available: unknown)
        output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 100, available: unknown)
        output:hdmi-surround71-extra1+input:analog-stereo: Digital Surround 7.1 (HDMI 2) Output + Analog Stereo Input (priority 160, available: unknown)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5200, available: unknown)
        output:hdmi-stereo-extra2+input:analog-stereo: Digital Stereo (HDMI 3) Output + Analog Stereo Input (priority 5260, available: unknown)
        output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 100, available: unknown)
        output:hdmi-surround-extra2+input:analog-stereo: Digital Surround 5.1 (HDMI 3) Output + Analog Stereo Input (priority 160, available: unknown)
        output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 100, available: unknown)
        output:hdmi-surround71-extra2+input:analog-stereo: Digital Surround 7.1 (HDMI 3) Output + Analog Stereo Input (priority 160, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:analog-stereo+input:analog-stereo>
    sinks:
        alsa_output.pci-0000_00_1f.3.analog-stereo/#0: Built-in Audio Analog Stereo
    sources:
        alsa_output.pci-0000_00_1f.3.analog-stereo.monitor/#0: Monitor of Built-in Audio Analog Stereo
        alsa_input.pci-0000_00_1f.3.analog-stereo/#1: Built-in Audio Analog Stereo
    ports:
        analog-input-internal-mic: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-headphone-mic: Microphone (priority 8700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-headset-mic: Headset Microphone (priority 8700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
```

---

### Post by jeremy31 on 2017-02-28
This is just strange, see what happens with
```
bluetoothctl
power on
connect 88:C6:26:EA:1D:1E
trust 88:C6:26:EA:1D:1E
exit
```

Post results ```
pactl list short | grep blue; pactl list-cards
```

---

### Post by Planetouched on 2017-03-03
Sorry for the delay and thanks again for your help!

Here are the outputs you required:

```
bluetoothctl
[NEW] Controller 9C:B6:D0:D3:FF:0E XXX-XPS-13-9360 [default]
[NEW] Device 88:C6:26:EA:1D:1E UE BOOM 2
[bluetooth]# power on
Changing power on succeeded
[CHG] Device 88:C6:26:EA:1D:1E Connected: no
[CHG] Device 88:C6:26:EA:1D:1E Connected: yes
[UE BOOM 2]# connect 88:C6:26:EA:1D:1E
Attempting to connect to 88:C6:26:EA:1D:1E
Failed to connect: org.bluez.Error.NotAvailable
[CHG] Device 88:C6:26:EA:1D:1E Connected: no
[CHG] Device 88:C6:26:EA:1D:1E Connected: yes
[UE BOOM 2]# trust 88:C6:26:EA:1D:1E
Changing 88:C6:26:EA:1D:1E trust succeeded
[CHG] Device 88:C6:26:EA:1D:1E Connected: no
[CHG] Device 88:C6:26:EA:1D:1E Connected: yes
[UE BOOM 2]# exit
[DEL] Controller 9C:B6:D0:D3:FF:0E XXX-XPS-13-9360 [default]


```


as well as:

```
pactl list short | grep blue; pactl list-cards
7    module-bluetooth-policy        
8    module-bluetooth-discover        
9    module-bluez5-discover        
No valid command specified.


```

---

### Post by goog64 on 2017-06-17
Planetouched, have you had any success with Bluetooth yet? I also have a Dell XPS13 and I have been trying for weeks to connect to my Amazon Echo speaker (or any bluetooth device actually), but all I get when I try to pair is "Failed to add device".

---

### Post by spirograph on 2017-10-08
I'm having a similar problem. UE BOOM 2 was connecting OK for a few days but now it doesn't always connect. And when it does, I don't see it as an Output device in Sound Settings.

I'm using the latest pulseaudio 1:8.0-0ubuntu3.4 which includes the recent bluetooth fixes on Linux Mint 18.2. The speaker is paired.

```
pactl list short | grep bluetooth7    module-bluetooth-policy        
8    module-bluetooth-discover    
```

From bluetoothctl:

```
[bluetooth]# connect C0:28:8D:45:76:DDAttempting to connect to C0:28:8D:45:76:DD
[CHG] Device C0:28:8D:45:76:DD Connected: yes
Connection successful
[UE BOOM 2]# info
Device C0:28:8D:45:76:DD
    Name: UE BOOM 2
    Alias: UE BOOM 2
    Class: 0x240418
    Icon: audio-card
    Paired: yes
    Trusted: yes
    Blocked: no
    Connected: yes
    LegacyPairing: no
    UUID: Unknown                   (000061fe-0000-1000-8000-00805f9b34fb)
    Modalias: bluetooth:v000ApFFFFdFFFF
    RSSI: -57

```

Under UUID I would expect to see Audio Sink and similar, but it only shows Unknown. It only stays connected for a few seconds then disconnects. It never appears as an Output Device.

The command posted by jeremy31 in post #10 here, gives an error: "You need to specify a profile by its name."

Update: After doing a factory reset on the UE BOOM 2 I now see: ```
[UE BOOM 2]# infoDevice C0:28:8D:45:76:DD
    Name: UE BOOM 2
    Alias: UE BOOM 2
    Class: 0x240418
    Icon: audio-card
    Paired: yes
    Trusted: yes
    Blocked: no
    Connected: yes
    LegacyPairing: no
    UUID: Serial Port               (00001101-0000-1000-8000-00805f9b34fb)
    UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
    UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: Handsfree                 (0000111e-0000-1000-8000-00805f9b34fb)
    UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
    UUID: Unknown                   (000061fe-0000-1000-8000-00805f9b34fb)
    Modalias: bluetooth:v000ApFFFFdFFFF
    RSSI: -44
[CHG] Device C0:28:8D:45:76:DD Connected: no
[CHG] Device C0:28:8D:45:76:DD Connected: yes
[CHG] Device C0:28:8D:45:76:DD Connected: no
[CHG] Device C0:28:8D:45:76:DD Connected: yes
[CHG] Device C0:28:8D:45:76:DD Connected: no
[CHG] Device C0:28:8D:45:76:DD Connected: yes
[CHG] Device C0:28:8D:45:76:DD Connected: no
[CHG] Device C0:28:8D:45:76:DD Connected: yes
[CHG] Device C0:28:8D:45:76:DD Connected: no
[CHG] Device C0:28:8D:45:76:DD Connected: yes
[CHG] Device C0:28:8D:45:76:DD Connected: no
[CHG] Device C0:28:8D:45:76:DD Connected: yes
```

But still I don't see the speaker added as an output device in sound settings. ```
pactl list cards short
0    alsa_card.pci-0000_00_1f.3    module-alsa-card.c

```

```
sudo systemctl status bluetooth.service

&#9679; bluetooth.service - Bluetooth service   Loaded: loaded (/lib/systemd/system/bluetooth.service; disabled; vendor preset: enabled)
   Active: active (running) since Sun 2017-10-08 22:59:50 CEST; 3s ago
     Docs: man:bluetoothd(8)
 Main PID: 3905 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;3905 /usr/lib/bluetooth/bluetoothd


Oct 08 22:59:50 john-hpenvy bluetoothd[3905]: Not enough free handles to register service
Oct 08 22:59:50 john-hpenvy bluetoothd[3905]: Current Time Service could not be registered
Oct 08 22:59:50 john-hpenvy bluetoothd[3905]: gatt-time-server: Input/output error (5)
Oct 08 22:59:50 john-hpenvy bluetoothd[3905]: Not enough free handles to register service
Oct 08 22:59:50 john-hpenvy bluetoothd[3905]: Not enough free handles to register service
Oct 08 22:59:50 john-hpenvy bluetoothd[3905]: Sap driver initialization failed.
Oct 08 22:59:50 john-hpenvy bluetoothd[3905]: sap-server: Operation not permitted (1)
Oct 08 22:59:50 john-hpenvy bluetoothd[3905]: Endpoint registered: sender=:1.52 path=/MediaEndpoint/A2DPSource
Oct 08 22:59:50 john-hpenvy bluetoothd[3905]: Endpoint registered: sender=:1.52 path=/MediaEndpoint/A2DPSink
Oct 08 22:59:50 john-hpenvy bluetoothd[3905]: Unable to register GATT service with handle 0x0001 for device C0:28:8D:45:76:DD

```

---

### Post by spirograph on 2017-10-16
It seems I was able to solve it today on my system. I was trying lots of things for days. Including running sudo hciconfig sspmode 0, adding my user to the lp group (sudo usermod -a -G lp <myuser>), and also installing PulseAudio 10 and Bluez 5.46 from the artful packages (bit messy). 

Maybe one of those fixed it, or maybe just luck.

I also noticed that the latest Ubuntu 17.10 Beta 2 had no problems connecting.

---

### Post by aromo2 on 2017-11-22
I had the same problem as reported in this thread (UE BOOM2 paired but not listed as a sound output device). This is how I got it to work:

1. Download latest bluez from [http://www.bluez.org](http://www.bluez.org)
2. Install pre-requisites:
```

sudo apt-get install glib2.0 libdbus-1-dev debhelper dh-autoreconf flex bison libdbus-glib-1-dev libglib2.0-dev  libcap-ng-dev libudev-dev libreadline-dev libical-dev check dh-systemd libebook1.2-dev

```
3. Install bluez:
```

tar xf bluez-<version>.tar.xz
cd bluez-<version>
./configure --prefix=/usr --mandir=/usr/share/man --sysconfdir=/etc --localstatedir=/var
make && make install
systemctl reboot

```

That's it. I hope it works for everybody else!

---

### Post by skitfish2 on 2018-07-29
Thank you so much, **aromo2**! I was trying for hours to get my UE Boom 2 working with two different laptops (Dell and Asus) both running Ubuntu 16.04, and the sound output device was *not* appearing. I followed your clear instructions and after a reboot it works perfectly on both laptops, using two different bluetooth chips!

Thanks again!

---

### Post by amez94 on 2019-03-05
It's working perfectly right now !
Thank you very much Dear sir :)

Additional information, the sound quality is pretty good ! (Thanks to the AD2P profile :))

Juste a tiny notice :

I had an error launching "make && make install" which has been solved using a single "make install" (without the first "make").

Good night ! (I'm french, it's about two hours in Paris)

---

