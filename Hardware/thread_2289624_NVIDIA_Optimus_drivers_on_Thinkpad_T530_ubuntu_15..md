---
title: "NVIDIA Optimus drivers on Thinkpad T530 ubuntu 15.04"
date: 2015-08-05
forum: Hardware
---

### Post by phun-ky on 2015-08-05
I'm having a hard time installing/activating the full power of the graphic cards on my Lenovo Thinkpad T530.

What I have done:

Activated the Optimus in the BIOS (set to optimus, and set the discovery option to enabled)

Installed linux generic headers and bumblebee, nvidia current (several versions) nvidia prime

I can run glxgears to get between 50-78ish fps, but when I run with optirun:

```
$ optirun glxgears
[  783.553776] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[  783.553807] [ERROR]Could not connect to bumblebee daemon - is it running?

```

This is my outputs: 

```
$ lsmod | grep -E 'nvidia|nouveau'
$ (nothing)

$ dpkg -l | grep '^ii' | grep nvidia
ii  bumblebee-nvidia                                     3.2.1-91~vividppa1                                    amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
ii  nvidia-346                                           346.87-0ubuntu0~xedgers15.04.1                        amd64        NVIDIA binary driver - version 346.87
ii  nvidia-opencl-icd-346                                346.87-0ubuntu0~xedgers15.04.1                        amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                         0.8.1                                                 amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                      355.06-0ubuntu0~xedgers15.04.1                        amd64        Tool for configuring the NVIDIA graphics driver

$ dmesg | grep -C3 -E 'nouveau|NVRM'
$ (nothing)

$ lspci -nn | grep '\[030[02]\]'
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [NVS 5400M] [10de:0def] (rev a1)


$ grep bumblebeed /var/log/syslog
Aug  5 18:01:54 alexander bumblebeed[3905]: [  313.792529] [INFO]/usr/sbin/bumblebeed 3.2.1 started
Aug  5 18:01:57 alexander bumblebeed[3905]: [  316.802330] [ERROR]Unloading nouveau driver timed out.
Aug  5 18:02:08 alexander bumblebeed[3905]: [  327.845082] [WARN]Received Terminated signal.
Aug  5 18:02:08 alexander bumblebeed[13269]: [  327.850785] [INFO]/usr/sbin/bumblebeed 3.2.1 started
Aug  5 18:02:45 alexander bumblebeed[854]: [   10.540875] [INFO]/usr/sbin/bumblebeed 3.2.1 started
Aug  5 18:03:59 alexander bumblebeed[854]: [   85.213251] [WARN]Received Terminated signal.
Aug  5 18:08:52 alexander bumblebeed[867]: [   13.698526] [INFO]/usr/sbin/bumblebeed 3.2.1 started
Aug  5 18:56:14 alexander bumblebeed[889]: [   11.413713] [INFO]/usr/sbin/bumblebeed 3.2.1 started
Aug  5 19:04:43 alexander bumblebeed[889]: modprobe: ERROR: ../libkmod/libkmod-module.c:816 kmod_module_insert_module() could not find module by name='off'
Aug  5 19:04:43 alexander bumblebeed[889]: modprobe: ERROR: could not insert 'off': Function not implemented
Aug  5 19:04:43 alexander bumblebeed[889]: [  520.606353] [ERROR]Module nouveau could not be loaded (timeout?)
Aug  5 19:04:43 alexander bumblebeed[889]: [  520.606363] [ERROR]Could not load GPU driver
Aug  5 19:09:50 alexander bumblebeed[889]: modprobe: ERROR: ../libkmod/libkmod-module.c:816 kmod_module_insert_module() could not find module by name='off'
Aug  5 19:09:50 alexander bumblebeed[889]: modprobe: ERROR: could not insert 'off': Function not implemented
Aug  5 19:09:50 alexander bumblebeed[889]: [  827.463655] [ERROR]Module nouveau could not be loaded (timeout?)
Aug  5 19:09:50 alexander bumblebeed[889]: [  827.463664] [ERROR]Could not load GPU driver
Aug  5 19:11:42 alexander bumblebeed[889]: modprobe: ERROR: ../libkmod/libkmod-module.c:816 kmod_module_insert_module() could not find module by name='off'
Aug  5 19:11:42 alexander bumblebeed[889]: modprobe: ERROR: could not insert 'off': Function not implemented
Aug  5 19:11:42 alexander bumblebeed[889]: [  939.833960] [ERROR]Module nouveau could not be loaded (timeout?)
Aug  5 19:11:42 alexander bumblebeed[889]: [  939.833967] [ERROR]Could not load GPU driver
Aug  5 19:13:34 alexander bumblebeed[889]: [ 1052.051487] [WARN]Received Terminated signal.
Aug  5 19:13:34 alexander bumblebeed[16679]: [ 1052.057471] [ERROR]Module 'nvidia' is not found.
Aug  5 19:13:34 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:13:34 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:13:34 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:14:20 alexander bumblebeed[911]: [   11.557940] [ERROR]Module 'nvidia' is not found.
Aug  5 19:14:20 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:14:20 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:14:20 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:15:20 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:15:20 alexander bumblebeed[2441]: [   71.647417] [ERROR]Module 'nvidia' is not found.
Aug  5 19:15:20 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:15:20 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:15:20 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:16:20 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:16:20 alexander bumblebeed[2498]: [  131.898182] [ERROR]Module 'nvidia' is not found.
Aug  5 19:16:20 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:16:20 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:16:20 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:17:21 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:17:21 alexander bumblebeed[2515]: [  192.147468] [ERROR]Module 'nvidia' is not found.
Aug  5 19:17:21 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:17:21 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:17:21 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:18:21 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:18:21 alexander bumblebeed[2529]: [  252.399851] [ERROR]Module 'nvidia' is not found.
Aug  5 19:18:21 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:18:21 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:18:21 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:19:21 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:19:21 alexander bumblebeed[2612]: [  312.647549] [ERROR]Module 'nvidia' is not found.
Aug  5 19:19:21 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:19:21 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:19:21 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:20:07 alexander bumblebeed[2642]: [  358.682057] [ERROR]Module 'nvidia_current' is not found.
Aug  5 19:20:07 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:20:07 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:20:07 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:20:35 alexander bumblebeed[2664]: [  386.830357] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:20:35 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:20:35 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:20:35 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:21:35 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:21:35 alexander bumblebeed[2676]: [  446.897200] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:21:35 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:21:35 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:21:35 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:22:36 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:22:36 alexander bumblebeed[14956]: [  507.147788] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:22:36 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:22:36 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:22:36 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:22:53 alexander bumblebeed[14973]: [  524.788139] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:22:53 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:22:53 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:22:53 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:23:37 alexander bumblebeed[870]: [   11.769999] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:23:37 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:23:37 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:23:37 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:24:36 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:24:36 alexander bumblebeed[2285]: [   71.897273] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:24:36 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:24:36 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:24:36 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:25:37 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:25:37 alexander bumblebeed[2606]: [  132.147556] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:25:37 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:25:37 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:25:37 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:26:37 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:26:37 alexander bumblebeed[2626]: [  192.399176] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:26:37 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:26:37 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:26:37 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:27:37 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:27:37 alexander bumblebeed[2641]: [  252.647439] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:27:37 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:27:37 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:27:37 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:28:37 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:28:37 alexander bumblebeed[15863]: [  312.897405] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:28:37 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:28:37 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:28:37 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:29:22 alexander bumblebeed[857]: [   11.219214] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:29:22 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:29:22 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:29:22 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:30:23 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:30:23 alexander bumblebeed[2172]: [   71.455648] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:30:23 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:30:23 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:30:23 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:31:23 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:31:23 alexander bumblebeed[2214]: [  131.705595] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:31:23 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:31:23 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:31:23 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:32:23 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:32:23 alexander bumblebeed[2330]: [  191.955416] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:32:23 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:32:23 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:32:23 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:33:23 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:33:23 alexander bumblebeed[2335]: [  252.205537] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:33:23 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:33:23 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:33:23 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:34:24 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:34:24 alexander bumblebeed[2344]: [  312.455537] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:34:24 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:34:24 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:34:24 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:35:24 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:35:24 alexander bumblebeed[2363]: [  372.706266] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:35:24 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:35:24 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:35:24 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:36:24 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:36:24 alexander bumblebeed[2374]: [  432.955905] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:36:24 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:36:24 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:36:24 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:37:24 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:37:24 alexander bumblebeed[2384]: [  493.205908] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:37:24 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:37:24 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:37:24 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:38:25 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:38:25 alexander bumblebeed[2392]: [  553.455470] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:38:25 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:38:25 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:38:25 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:39:25 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:39:25 alexander bumblebeed[2410]: [  613.705528] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:39:25 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:39:25 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:39:25 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:40:25 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:40:25 alexander bumblebeed[2421]: [  673.955931] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:40:25 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:40:25 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:40:25 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:41:25 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:41:25 alexander bumblebeed[2427]: [  734.205405] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:41:25 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:41:25 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:41:25 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:42:26 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:42:26 alexander bumblebeed[2436]: [  794.456087] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:42:26 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:42:26 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:42:26 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:43:26 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:43:26 alexander bumblebeed[2445]: [  854.705900] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:43:26 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:43:26 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:43:26 alexander systemd[1]: bumblebeed.service failed.
Aug  5 19:44:26 alexander systemd[1]: bumblebeed.service holdoff time over, scheduling restart.
Aug  5 19:44:26 alexander bumblebeed[2462]: [  914.955621] [ERROR]Module 'nvidia-current' is not found.
Aug  5 19:44:26 alexander systemd[1]: bumblebeed.service: main process exited, code=exited, status=1/FAILURE
Aug  5 19:44:26 alexander systemd[1]: Unit bumblebeed.service entered failed state.
Aug  5 19:44:26 alexander systemd[1]: bumblebeed.service failed.


```

Here is the additional drivers dialog:

[IMG]http://i.imgur.com/6DI1XMQ.png[/IMG]


Anyone got an idea on what I can do to fix this? Need more information on this? Any help would be greatly appreciated! ;)

---

### Post by efflandt on 2015-08-07
I think bumblebee and nvidia-prime are mutually exclusive. Or at least since nvidia-prime in 14.04 there is no need for bumblebee for hybrid Intel/Nvidia graphics. With bumblebee, optirun would feed nvidia through Intel graphics to the screen. With nvidia-prime I believe it is direct.

With nvidia-prime you select which graphics you want to use from **NVIDIA X Server Settings**. If switching from Nvidia to Intel you have to log out of X and log back in. Although, to switch from Intel to Nvidia, I have to reboot my laptop. Contrary to **nomodeset** boot parameter typically needed for Nvidia on a desktop PC, someone could not get their system to work properly on hybrid graphics laptop unless they did NOT use it. So I did not use nomodeset when I installed 14.04 on laptop in my sig, and it all works fine (including Steam games).

When I ran Ubuntu 13.10 where only bumblebee seemed to work, I had to add launch options for steam games before the optirun command. But in 14.04 with nvidia-prime I do not need any game launch parameters.

My laptop has an older nvidia chip, so it is just using nvidia-331-updates from normal repos. My desktop is using nvidia-352 from xorg-edgers ppa.

---

