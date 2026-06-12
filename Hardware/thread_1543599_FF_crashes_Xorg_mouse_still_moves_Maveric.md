---
title: "FF crashes Xorg mouse still moves Maveric"
date: 2010-08-01
forum: Hardware
---

### Post by Kangarooo on 2010-08-01
on 10.04 i had this crash. [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/587710](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/587710) since no response im now reinstalled 10.10 to test if no xorg crashes.. 
im actually having now different crash.. all screen freezes and network also. mouse still moves. with raw mode i can open tty6 (still not showing in screen) and making ctrl+alt+del restart.. what dbg i should install? i have nVidia Corporation NV34 [GeForce FX 5500] (rev a1) but restricted driver i removed couse that makes screen respond slow.. so restricted not installed.

happens when in FF opening YT video (not all but most makes this crash) or [http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#cite_note-11](http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#cite_note-11) if i open without citenote then it doesnt hang. opening cite note makes screen go to cite note and its marked blue till blue fades out..
what should i install to debug X and post report couse i cant get any crash report when crashes happen. for FF ive found firefox-gdb and its installed but for X?

for now i did gdb -p $(pidof firefox-bin) -batch -ex 'handle all nostop' -ex 'handle all pass' -ex 'handle 11 stop' -ex 'cont' -ex 'bt full' -ex 'cont' > /opt/ffcrash.txt 2>&1
and
gdb -p $(pidof X) -batch -ex 'handle all nostop' -ex 'handle all pass' -ex 'handle 11 stop' -ex 'cont' -ex 'bt full' -ex 'cont' > /opt/xservercrash.txt 2>&1


heres they outputs:

1st i run only about X and when opened wikipedia link this was output after restart.

xservercrash1.txt:
```

[Thread debugging using libthread_db enabled]
0x00d8c416 in __kernel_vsyscall ()

Program received signal SIGUSR1, User defined signal 1.

Program received signal SIGTERM, Terminated.
Detaching from program: /usr/bin/Xorg, process 800
```

then i used both toghether and heres outputs of both running toghether till crash:
p.s. when running theese then i can even open one YT video and that Wiki link and only later crash hapens. without gdb running this happens immidiattly.

ffcrash2.txt
```

[Thread debugging using libthread_db enabled]
[New Thread 0xb108cb70 (LWP 1632)]
[New Thread 0xac1c7b70 (LWP 1567)]
[New Thread 0xb69ffb70 (LWP 1566)]
[New Thread 0xb226bb70 (LWP 1565)]
[New Thread 0xb188db70 (LWP 1564)]
[New Thread 0xb4dffb70 (LWP 1559)]
[New Thread 0xb59fdb70 (LWP 1558)]
[New Thread 0xb61feb70 (LWP 1557)]
[New Thread 0xb7399b70 (LWP 1555)]
0x00843416 in __kernel_vsyscall ()
[New Thread 0xa7dfeb70 (LWP 2105)]
[New Thread 0xa6dfcb70 (LWP 2108)]
[New Thread 0xaabffb70 (LWP 2109)]
[Thread 0xaabffb70 (LWP 2109) exited]
[New Thread 0xaabffb70 (LWP 2110)]
[Thread 0xa7dfeb70 (LWP 2105) exited]
[New Thread 0xa7dfeb70 (LWP 2111)]
[Thread 0xa7dfeb70 (LWP 2111) exited]
[New Thread 0xa7dfeb70 (LWP 2112)]
[New Thread 0xa85ffb70 (LWP 2113)]
[New Thread 0xa61ffb70 (LWP 2114)]
[Thread 0xa61ffb70 (LWP 2114) exited]
[New Thread 0xa61ffb70 (LWP 2115)]
[Thread 0xa61ffb70 (LWP 2115) exited]
[New Thread 0xa61ffb70 (LWP 2116)]
[Thread 0xa61ffb70 (LWP 2116) exited]
[New Thread 0xa61ffb70 (LWP 2117)]
[New Thread 0xa4f1ab70 (LWP 2118)]
[Thread 0xaabffb70 (LWP 2110) exited]
[New Thread 0xa4719b70 (LWP 2119)]
[Thread 0xa4f1ab70 (LWP 2118) exited]
[Thread 0xa61ffb70 (LWP 2117) exited]
[New Thread 0xaabffb70 (LWP 2120)]
[Thread 0xaabffb70 (LWP 2120) exited]
[New Thread 0xaabffb70 (LWP 2121)]
[Thread 0xaabffb70 (LWP 2121) exited]
[New Thread 0xaabffb70 (LWP 2125)]
[Thread 0xaabffb70 (LWP 2125) exited]
[New Thread 0xaabffb70 (LWP 2126)]
[Thread 0xaabffb70 (LWP 2126) exited]
[New Thread 0xaabffb70 (LWP 2127)]
[Thread 0xaabffb70 (LWP 2127) exited]
[New Thread 0xaabffb70 (LWP 2128)]
[Thread 0xaabffb70 (LWP 2128) exited]
[New Thread 0xaabffb70 (LWP 2129)]
[Thread 0xaabffb70 (LWP 2129) exited]
[New Thread 0xaabffb70 (LWP 2130)]
[Thread 0xaabffb70 (LWP 2130) exited]
[New Thread 0xaabffb70 (LWP 2131)]
[Thread 0xaabffb70 (LWP 2131) exited]
[Thread 0xa4719b70 (LWP 2119) exited]
Detaching from program: /usr/lib/firefox-3.6.8/firefox-bin, process 1554

```


xservercrash2.txt:
```

[Thread debugging using libthread_db enabled]
0x00f76416 in __kernel_vsyscall ()

Program received signal SIGUSR1, User defined signal 1.

Program received signal SIGUSR1, User defined signal 1.

Program received signal SIGUSR1, User defined signal 1.

Program received signal SIGTERM, Terminated.
Detaching from program: /usr/bin/Xorg, process 818
```

---

### Post by lovinglinux on 2010-08-01
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Kangarooo on 2010-08-02
> **lovinglinux said:**
> [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

I have already correct flash installed- flashplugin-nonfree and to avoid some crashes ive disabled flash in FF for now. Also without flash enabled opening ur link again comp crashed..

---

