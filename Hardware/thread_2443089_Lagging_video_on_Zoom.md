---
title: "Lagging video on Zoom"
date: 2020-05-11
forum: Hardware
---

### Post by hosie123 on 2020-05-11
I've upgraded to Ubuntu 20. on my desktop and my Zoom video operates very slow/lagging. The camera is new and works well on other chat platforms as well as the Cheese program. I've tried this on Ububtu vs. 18 and 19 as well as Mint. Any ideas?

---

### Post by Autodave on 2020-05-11
How bad is the lagging?  Is the sound just a little behind the video?  I have noticed that the audio is always about 1/2 second behind.  If your internet connection / band width is poor, the lag will be greater.

---

### Post by SeijiSensei on 2020-05-11
The performance of a Zoom session seems to depend on the bandwidth available to the host.  If you have a decent-sized pipe to the Internet and are using wifi, I'd try hard-wiring the computer to your router with an Ethernet cable. One friend had to upgrade his Internet connection to a higher speed to host Zoom meetings.

---

### Post by hosie123 on 2020-05-11
Thanks for your replies, I notice that the video lags behind in my movements, almost slow motion. I am connected via ethernet and have a download speed of 300 mbs. Shouldn't need more than that, right.

---

### Post by DuckHook on 2020-05-11
If the problem is *your* broadcast quality, then it's your *upload* speed that matters. However, there are so many factors that come into play that one cannot simply nail any one factor down as the culprit. I rather doubt that the issue is even network related because you state that your other chat platforms are fine. Perhaps Zoom's servers are being overloaded due to&#8230; well, the state of affairs in the world today. Perhaps those other chat platforms still have capacity, or are point-to-point so they avoid servers entirely. Without a detailed analysis, it's hard to say.

---

### Post by hosie123 on 2020-05-12
Thanks again. I would agree that it's not network related. Zoom works fine on other computers in my home (all wifi connected) , although they are running windows or on the Chrome book. What detailed analysis are you referring to?

---

### Post by DuckHook on 2020-05-14
> **hosie123 said:**
> &#8230;What detailed analysis are you referring to?
I do not use Zoom, so cannot advise you except with very general suggestions:

[LIST=1]
[*]Most apps can be put into debug mode. This generates reams of data, but usually includes useful info.
[*]Find where Zoom writes its logs and have a look through them.
[*]What does dmesg, syslog and journalctl say?
[/LIST]
Aside from these typical places to look, I'm afraid I can't be of further help.

---

### Post by ajgreeny on 2020-05-14
I use zoom where there is no available alternative and I agree that the video lag can be a major problem, particularly if any music is used and where it needs to sync with the visuals.

From what I hear from other users this is a known, and apparently unsolvable problem whether using Windows, Mac or Linux; everybody talks about the problem but as for answers, I'm  afraid they have been totally lacking.

Have you queried the zoom developers or looked on any forums other than this one?

---

### Post by SeijiSensei on 2020-05-14
I was in a chat just this past weekend with over 25 participants using the Linux client. I saw no video lag at all.  I am on a connection with 200 MBit down though.

---

### Post by ajgreeny on 2020-05-14
I suspect the host of the last meeting I was involved in uses a standard ADSL broadband therefore with a speed of probably 17-25 Mb/s down and a very slow rate up.

Even that was not too bad so far as the lag is concerned, but there is a distinct lag where it's being used for one group needing music and movement, which needs to sync but in fast music tracks can easily be a whole beat out of sync.

I assume it will also depend on the video settings used on machines, with HD video presumably making matters worse.

---

### Post by hosie123 on 2020-05-17
Thanks to all your responses. I just installed Win 10 to dual boot my machine and zoom works fine with it. When I revert back to linux, my view of my video still lags. Something off w the hardware combo I suppose. Oh well. Must use Windows in a pinch.

---

### Post by CelticWarrior on 2020-05-17
What you're interpreting as "lag" may well be an inadequate graphics driver. You never actually posted your hardware specifications and nobody asked... I guess now it's too late.

---

### Post by hosie123 on 2020-05-18
Not too late. Always interested in figuring things out. But if the driver doesn't work on linux why would it work fine on windows. What specs would you like to see to help w this.

---

### Post by ajgreeny on 2020-05-19
> **hosie123 said:**
> Not too late. Always interested in figuring things out. But if the driver doesn't work on linux why would it work fine on windows. What specs would you like to see to help w this.
Because  Linux isn't  Windows  and uses different drivers for the same hardware.

For a start show us the output of terminal, command 
inxi -Fzx

---

### Post by hosie123 on 2020-05-19
Thanks, that command doesn't work on Mint. Should I go to the Mint forum?

---

### Post by ajgreeny on 2020-05-19
Sorry!
I typed that command using an android tablet and the google-keyboard autocorrected the command to an upper case first letter ***Inxi -Fzx***; it should have been a lower case ***inxi -Fzx***

---

### Post by hosie123 on 2020-05-24
here's the output:

System:
  Host: sjoseph-OptiPlex-755 Kernel: 4.15.0-101-generic x86_64 bits: 64 
  compiler: gcc v: 7.5.0 Desktop: Cinnamon 4.4.8 
  Distro: Linux Mint 19.3 Tricia base: Ubuntu 18.04 bionic 
Machine:
  Type: Desktop System: Dell product: OptiPlex 755 v: N/A serial: <filter> 
  Mobo: Dell model: 0PU052 serial: <filter> BIOS: Dell v: A21 
  date: 12/07/2011 
CPU:
  Topology: Dual Core model: Intel Core2 Duo E6750 bits: 64 type: MCP 
  arch: Core Merom rev: B L2 cache: 4096 KiB 
  flags: lm nx pae sse sse2 sse3 ssse3 vmx bogomips: 10639 
  Speed: 2047 MHz min/max: N/A Core speeds (MHz): 1: 2047 2: 2006 
Graphics:
  Device-1: Intel 82Q35 Express Integrated Graphics 
  vendor: Dell OptiPlex 755 driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.19.6 driver: intel 
  unloaded: fbdev,modesetting,vesa resolution: 1600x900~60Hz 
  OpenGL: renderer: Mesa DRI Intel Q35 v: 1.4 Mesa 19.2.8 direct render: Yes 
Audio:
  Device-1: Intel 82801I HD Audio vendor: Dell Optiplex 755 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Device-2: Sunplus Innovation type: USB driver: snd-usb-audio,uvcvideo 
  bus ID: 1-2:2 
  Sound Server: ALSA v: k4.15.0-101-generic 
Network:
  Device-1: Intel 82566DM-2 Gigabit Network vendor: Dell OptiPlex 755 
  driver: e1000e v: 3.2.6-k port: ecc0 bus ID: 00:19.0 
  IF: enp0s25 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 227.39 GiB used: 27.99 GiB (12.3%) 
  ID-1: /dev/sda vendor: Kingston model: SA400S37240G size: 223.57 GiB 
  ID-2: /dev/sdb type: USB vendor: HP model: c310w size: 3.82 GiB 
Partition:
  ID-1: / size: 130.23 GiB used: 27.78 GiB (21.3%) fs: ext4 dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 35.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 182 Uptime: 3h 13m Memory: 6.67 GiB used: 1.87 GiB (28.0%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.5.0 Shell: bash v: 4.4.20 
  inxi: 3.0.32

---

