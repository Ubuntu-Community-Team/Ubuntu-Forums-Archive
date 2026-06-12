---
title: "Java OpenGL Trouble"
date: 2008-08-15
forum: General Help
---

### Post by furuno on 2008-08-15
Hello.

I'm currently having a problem with my new installation after I've upgraded my PC. I'm using Ubuntu 8.04.1 with the 2.6.24-19-generic kernel.

The problem is, everytime I've tried to run a program (game, to be more specific) I've developed with Java, it gives me this error :

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f2a84b06330, pid=5948, tid=1089845584
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x7c330]  memset+0x60
#
# An error report file with more information is saved as:
# /media/Data-0/Pekerjaan/Program/SimpleJOGL/hs_err_pid5948.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Java Result: 134
BUILD SUCCESSFUL (total time: 3 seconds)
```And here's the content of the error log file :
```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f2a84b06330, pid=5948, tid=1089845584
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x7c330]  memset+0x60
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x0000000040112800):  JavaThread "main" [_thread_in_native, id=5949, stack(0x0000000040e5b000,0x0000000040f5c000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x0000000054226ac0

Registers:
RAX=0x00000000000002ca, RBX=0x0000000054226ac0, RCX=0x0000000054226ac0, RDX=0x000000000000b280
RSP=0x0000000040f582c8, RBP=0x00007f2a54226ab0, RSI=0x0000000000000000, RDI=0x0000000054226ac0
R8 =0x0000000000000000, R9 =0x0000000000000000, R10=0x00007f2a541b4260, R11=0x0000000000000206
R12=0x00007f2a540e50a0, R13=0x00007f2a540e50a0, R14=0x0000000000000000, R15=0x00007f2a540bc4a0
RIP=0x00007f2a84b06330, EFL=0x0000000000010287, CSGSFS=0x0000000000000033, ERR=0x0000000000000006
  TRAPNO=0x000000000000000e

Top of Stack: (sp=0x0000000040f582c8)
0x0000000040f582c8:   00007f2a53094073 00007f2a5411ead0
0x0000000040f582d8:   00007f2a5411ead0 00007f2a54225040
0x0000000040f582e8:   00007f2a5304e246 0000000040f58360
0x0000000040f582f8:   00007f2a540d6e50 00007f2a540e50a0
0x0000000040f58308:   00007f2a540d6e90 00007f2a540d6d40
0x0000000040f58318:   0000000000000000 00007f2a540bc540
0x0000000040f58328:   00007f2a540d9620 00007f2a540d6e50
0x0000000040f58338:   00007f2a540e50a0 00007f2a540d6e90
0x0000000040f58348:   00007f2a540d6d40 00007f2a540bc4a0
0x0000000040f58358:   00007f2a53653b5f 00007f2a00000092
0x0000000040f58368:   00007f2a540d6e50 00007f2a540bc4a0
0x0000000040f58378:   00007f2a540d9620 00007f2a540bc4a0
0x0000000040f58388:   00007f2a53667378 0000000000000000
0x0000000040f58398:   0000000000000000 0000000000000000
0x0000000040f583a8:   0000000000000000 0000000000000000
0x0000000040f583b8:   0000000000000000 0000000000000000
0x0000000040f583c8:   0000000000000000 0000000000000000
0x0000000040f583d8:   0000000000000000 0000000000000000
0x0000000040f583e8:   0000000000000000 0000000000000000
0x0000000040f583f8:   0000000000000000 0000000000000000
0x0000000040f58408:   0000000000000000 0000000000000000
0x0000000040f58418:   0000000000000000 0000000000000000
0x0000000040f58428:   0000000000000000 0000000000000000
0x0000000040f58438:   0000000000000000 0000000000000000
0x0000000040f58448:   0000000000000000 0000000000000000
0x0000000040f58458:   0000000000000000 0000000000000000
0x0000000040f58468:   0000000000000000 0000000000000000
0x0000000040f58478:   0000000000000000 0000000000000000
0x0000000040f58488:   0000000000000000 0000000000000000
0x0000000040f58498:   0000000000000000 0000000000000000
0x0000000040f584a8:   0000000000000000 0000000000000000
0x0000000040f584b8:   0000000000000001 0000000000000000 

Instructions: (pc=0x00007f2a84b06330)
0x00007f2a84b06320:   00 73 6d 66 66 66 66 2e 0f 1f 84 00 00 00 00 00
0x00007f2a84b06330:   4c 89 01 4c 89 41 08 4c 89 41 10 4c 89 41 18 4c 

Stack: [0x0000000040e5b000,0x0000000040f5c000],  sp=0x0000000040f582c8,  free space=1012k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libc.so.6+0x7c330]  memset+0x60

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x00007f2a54089800 JavaThread "AWT-XAWT" daemon [_thread_blocked, id=5961, stack(0x000000004115e000,0x000000004125f000)]
  0x00007f2a54032c00 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=5960, stack(0x000000004105d000,0x000000004115e000)]
  0x00000000401abc00 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=5958, stack(0x0000000041cd1000,0x0000000041dd2000)]
  0x00000000401a9400 JavaThread "CompilerThread1" daemon [_thread_blocked, id=5957, stack(0x0000000041bd0000,0x0000000041cd1000)]
  0x00000000401a5c00 JavaThread "CompilerThread0" daemon [_thread_blocked, id=5956, stack(0x0000000041acf000,0x0000000041bd0000)]
  0x00000000401a4400 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=5955, stack(0x00000000419ce000,0x0000000041acf000)]
  0x0000000040178c00 JavaThread "Finalizer" daemon [_thread_blocked, id=5954, stack(0x00000000418cd000,0x00000000419ce000)]
  0x0000000040177800 JavaThread "Reference Handler" daemon [_thread_blocked, id=5953, stack(0x00000000417cc000,0x00000000418cd000)]
=>0x0000000040112800 JavaThread "main" [_thread_in_native, id=5949, stack(0x0000000040e5b000,0x0000000040f5c000)]

Other Threads:
  0x0000000040172400 VMThread [stack: 0x0000000041fc9000,0x00000000420ca000] [id=5952]
  0x00000000401ad800 WatcherThread [stack: 0x0000000041dd2000,0x0000000041ed3000] [id=5959]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 9408K, used 6753K [0x00007f2a757e0000, 0x00007f2a76260000, 0x00007f2a7ffe0000)
  eden space 8064K, 83% used [0x00007f2a757e0000,0x00007f2a75e787d0,0x00007f2a75fc0000)
  from space 1344K, 0% used [0x00007f2a76110000,0x00007f2a76110000,0x00007f2a76260000)
  to   space 1344K, 0% used [0x00007f2a75fc0000,0x00007f2a75fc0000,0x00007f2a76110000)
 PSOldGen        total 21504K, used 0K [0x00007f2a607e0000, 0x00007f2a61ce0000, 0x00007f2a757e0000)
  object space 21504K, 0% used [0x00007f2a607e0000,0x00007f2a607e0000,0x00007f2a61ce0000)
 PSPermGen       total 21248K, used 9512K [0x00007f2a5b3e0000, 0x00007f2a5c8a0000, 0x00007f2a607e0000)
  object space 21248K, 44% used [0x00007f2a5b3e0000,0x00007f2a5bd2a0f8,0x00007f2a5c8a0000)

Dynamic libraries:
40000000-40009000 r-xp 00000000 07:00 375392                             /usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/java
40108000-4010a000 rwxp 00008000 07:00 375392                             /usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/java
4010a000-406e4000 rwxp 4010a000 00:00 0                                  [heap]
40d0a000-40d0b000 ---p 40d0a000 00:00 0 
40d0b000-40e0b000 rwxp 40d0b000 00:00 0 
40e5b000-40e5e000 ---p 40e5b000 00:00 0 
40e5e000-40f5c000 rwxp 40e5e000 00:00 0 
40f5c000-40f5d000 ---p 40f5c000 00:00 0 
40f5d000-4105d000 rwxp 40f5d000 00:00 0 
4105d000-41060000 ---p 4105d000 00:00 0 
41060000-4115e000 rwxp 41060000 00:00 0 
4115e000-41161000 ---p 4115e000 00:00 0 
41161000-4125f000 rwxp 41161000 00:00 0 
417cc000-417cf000 ---p 417cc000 00:00 0 
417cf000-418cd000 rwxp 417cf000 00:00 0 
418cd000-418d0000 ---p 418cd000 00:00 0 
418d0000-419ce000 rwxp 418d0000 00:00 0 
419ce000-419d1000 ---p 419ce000 00:00 0 
419d1000-41acf000 rwxp 419d1000 00:00 0 
41acf000-41ad2000 ---p 41acf000 00:00 0 
41ad2000-41bd0000 rwxp 41ad2000 00:00 0 
41bd0000-41bd3000 ---p 41bd0000 00:00 0 
41bd3000-41cd1000 rwxp 41bd3000 00:00 0 
41cd1000-41cd4000 ---p 41cd1000 00:00 0 
41cd4000-41dd2000 rwxp 41cd4000 00:00 0 
41dd2000-41dd3000 ---p 41dd2000 00:00 0 
41dd3000-41ed3000 rwxp 41dd3000 00:00 0 
41fc9000-41fca000 ---p 41fc9000 00:00 0 
41fca000-420ca000 rwxp 41fca000 00:00 0 
7f2a42b79000-7f2a42f3e000 rwxp 7f2a42b79000 00:00 0 
7f2a42f3e000-7f2a52f3e000 rwxs 00003000 00:0e 14016                      /dev/dri/card0
7f2a52f3e000-7f2a53cb2000 r-xp 00000000 07:00 81667                      /usr/lib/dri/fglrx_dri.so
7f2a53cb2000-7f2a53db2000 ---p 00d74000 07:00 81667                      /usr/lib/dri/fglrx_dri.so
7f2a53db2000-7f2a53e54000 rwxp 00d74000 07:00 81667                      /usr/lib/dri/fglrx_dri.so
7f2a53e54000-7f2a54232000 rwxp 7f2a53e54000 00:00 0 
7f2a54232000-7f2a58000000 ---p 7f2a54232000 00:00 0 
7f2a580b8000-7f2a58302000 rwxp 7f2a580b8000 00:00 0 
7f2a58313000-7f2a58a13000 rwxs 00006000 00:0e 14016                      /dev/dri/card0
7f2a58a13000-7f2a58a23000 rwxs 00005000 00:0e 14016                      /dev/dri/card0
7f2a58a23000-7f2a58a25000 rwxs 00002000 00:0e 14016                      /dev/dri/card0
7f2a58a25000-7f2a58a45000 rwxp 7f2a58a25000 00:00 0 
7f2a58a45000-7f2a58a47000 r-xp 00000000 07:00 421215                     /home/furuno/.netbeans/6.1/jogl-runtime/jogl.jar-natives-linux-amd64/libjogl_awt.so
7f2a58a47000-7f2a58b46000 ---p 00002000 07:00 421215                     /home/furuno/.netbeans/6.1/jogl-runtime/jogl.jar-natives-linux-amd64/libjogl_awt.so
7f2a58b46000-7f2a58b47000 rwxp 00001000 07:00 421215                     /home/furuno/.netbeans/6.1/jogl-runtime/jogl.jar-natives-linux-amd64/libjogl_awt.so
7f2a58b47000-7f2a58b48000 r-xp 00000000 07:00 375438                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libjawt.so
7f2a58b48000-7f2a58c47000 ---p 00001000 07:00 375438                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libjawt.so
7f2a58c47000-7f2a58c48000 rwxp 00000000 07:00 375438                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libjawt.so
7f2a58c48000-7f2a58c4d000 r-xp 00000000 07:00 82616                      /usr/lib/libXxf86vm.so.1.0.0
7f2a58c4d000-7f2a58e4c000 ---p 00005000 07:00 82616                      /usr/lib/libXxf86vm.so.1.0.0
7f2a58e4c000-7f2a58e4d000 rwxp 00004000 07:00 82616                      /usr/lib/libXxf86vm.so.1.0.0
7f2a58e4d000-7f2a58f3c000 r-xp 00000000 07:00 421214                     /home/furuno/.netbeans/6.1/jogl-runtime/jogl.jar-natives-linux-amd64/libjogl.so
7f2a58f3c000-7f2a5903c000 ---p 000ef000 07:00 421214                     /home/furuno/.netbeans/6.1/jogl-runtime/jogl.jar-natives-linux-amd64/libjogl.so
7f2a5903c000-7f2a5903d000 rwxp 000ef000 07:00 421214                     /home/furuno/.netbeans/6.1/jogl-runtime/jogl.jar-natives-linux-amd64/libjogl.so
7f2a5903d000-7f2a59046000 r-xs 00000000 07:00 181642                     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
7f2a59046000-7f2a5904a000 r-xs 00000000 07:00 181643                     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
7f2a5904a000-7f2a59053000 r-xs 00000000 07:00 182035                     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
7f2a59053000-7f2a59056000 r-xs 00000000 07:00 181649                     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
7f2a59056000-7f2a59061000 r-xs 00000000 07:00 181653                     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
7f2a59061000-7f2a59091000 rwxp 7f2a59061000 00:00 0 
7f2a59091000-7f2a59113000 r-xp 00000000 07:00 81662                      /usr/lib/libGL.so.1.2
7f2a59113000-7f2a59212000 ---p 00082000 07:00 81662                      /usr/lib/libGL.so.1.2
7f2a59212000-7f2a5921d000 rwxp 00081000 07:00 81662                      /usr/lib/libGL.so.1.2
7f2a5921d000-7f2a59222000 rwxp 7f2a5921d000 00:00 0 
7f2a59222000-7f2a59223000 r-xp 00000000 07:00 421257                     /home/furuno/.netbeans/6.1/gluegen-runtime/gluegen-rt.jar-natives-linux-amd64/libgluegen-rt.so
7f2a59223000-7f2a59322000 ---p 00001000 07:00 421257                     /home/furuno/.netbeans/6.1/gluegen-runtime/gluegen-rt.jar-natives-linux-amd64/libgluegen-rt.so
7f2a59322000-7f2a59323000 rwxp 00000000 07:00 421257                     /home/furuno/.netbeans/6.1/gluegen-runtime/gluegen-rt.jar-natives-linux-amd64/libgluegen-rt.so
7f2a59323000-7f2a59328000 r-xp 00000000 07:00 82582                      /usr/lib/libXfixes.so.3.1.0
7f2a59328000-7f2a59527000 ---p 00005000 07:00 82582                      /usr/lib/libXfixes.so.3.1.0
7f2a59527000-7f2a59528000 rwxp 00004000 07:00 82582                      /usr/lib/libXfixes.so.3.1.0
7f2a59528000-7f2a59531000 r-xp 00000000 07:00 82602                      /usr/lib/libXrender.so.1.3.0
7f2a59531000-7f2a59730000 ---p 00009000 07:00 82602                      /usr/lib/libXrender.so.1.3.0
7f2a59730000-7f2a59731000 rwxp 00008000 07:00 82602                      /usr/lib/libXrender.so.1.3.0
7f2a59731000-7f2a5973a000 r-xp 00000000 07:00 82572                      /usr/lib/libXcursor.so.1.0.2
7f2a5973a000-7f2a5993a000 ---p 00009000 07:00 82572                      /usr/lib/libXcursor.so.1.0.2
7f2a5993a000-7f2a5993b000 rwxp 00009000 07:00 82572                      /usr/lib/libXcursor.so.1.0.2
7f2a5993b000-7f2a5994c000 rwxp 7f2a5993b000 00:00 0 
7f2a5994c000-7f2a599ca000 r-xp 00000000 07:00 375422                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libfontmanager.so
7f2a599ca000-7f2a59ac9000 ---p 0007e000 07:00 375422                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libfontmanager.so
7f2a59ac9000-7f2a59adf000 rwxp 0007d000 07:00 375422                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libfontmanager.so
7f2a59adf000-7f2a59af0000 rwxp 7f2a59adf000 00:00 0 
7f2a59af0000-7f2a59af5000 r-xp 00000000 07:00 82576                      /usr/lib/libXdmcp.so.6.0.0
7f2a59af5000-7f2a59cf4000 ---p 00005000 07:00 82576                      /usr/lib/libXdmcp.so.6.0.0
7f2a59cf4000-7f2a59cf5000 rwxp 00004000 07:00 82576                      /usr/lib/libXdmcp.so.6.0.0
7f2a59cf5000-7f2a59d10000 r-xp 00000000 07:00 83404                      /usr/lib/libxcb.so.1.0.0
7f2a59d10000-7f2a59f0f000 ---p 0001b000 07:00 83404                      /usr/lib/libxcb.so.1.0.0
7f2a59f0f000-7f2a59f10000 rwxp 0001a000 07:00 83404                      /usr/lib/libxcb.so.1.0.0
7f2a59f10000-7f2a59f11000 r-xp 00000000 07:00 83402                      /usr/lib/libxcb-xlib.so.0.0.0
7f2a59f11000-7f2a5a110000 ---p 00001000 07:00 83402                      /usr/lib/libxcb-xlib.so.0.0.0
7f2a5a110000-7f2a5a111000 rwxp 00000000 07:00 83402                      /usr/lib/libxcb-xlib.so.0.0.0
7f2a5a111000-7f2a5a113000 r-xp 00000000 07:00 82565                      /usr/lib/libXau.so.6.0.0
7f2a5a113000-7f2a5a312000 ---p 00002000 07:00 82565                      /usr/lib/libXau.so.6.0.0
7f2a5a312000-7f2a5a313000 rwxp 00001000 07:00 82565                      /usr/lib/libXau.so.6.0.0
7f2a5a313000-7f2a5a31c000 r-xp 00000000 07:00 82588                      /usr/lib/libXi.so.6.0.0
7f2a5a31c000-7f2a5a51b000 ---p 00009000 07:00 82588                      /usr/lib/libXi.so.6.0.0
7f2a5a51b000-7f2a5a51c000 rwxp 00008000 07:00 82588                      /usr/lib/libXi.so.6.0.0
7f2a5a51c000-7f2a5a521000 r-xp 00000000 07:00 82608                      /usr/lib/libXtst.so.6.1.0
7f2a5a521000-7f2a5a721000 ---p 00005000 07:00 82608                      /usr/lib/libXtst.so.6.1.0
7f2a5a721000-7f2a5a722000 rwxp 00005000 07:00 82608                      /usr/lib/libXtst.so.6.1.0
7f2a5a722000-7f2a5a821000 r-xp 00000000 07:00 82559                      /usr/lib/libX11.so.6.2.0
7f2a5a821000-7f2a5aa20000 ---p 000ff000 07:00 82559                      /usr/lib/libX11.so.6.2.0
7f2a5aa20000-7f2a5aa25000 rwxp 000fe000 07:00 82559                      /usr/lib/libX11.so.6.2.0
7f2a5aa25000-7f2a5aa36000 r-xp 00000000 07:00 82580                      /usr/lib/libXext.so.6.4.0
7f2a5aa36000-7f2a5ac35000 ---p 00011000 07:00 82580                      /usr/lib/libXext.so.6.4.0
7f2a5ac35000-7f2a5ac36000 rwxp 00010000 07:00 82580                      /usr/lib/libXext.so.6.4.0
7f2a5ac36000-7f2a5ac3c000 rwxp 7f2a5ac36000 00:00 0 
7f2a5ac3c000-7f2a5ac47000 r-xs 00000000 07:00 181632                     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
7f2a5ac47000-7f2a5ac86000 r-xp 00000000 07:00 375412                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/xawt/libmawt.so
7f2a5ac86000-7f2a5ad87000 ---p 0003f000 07:00 375412                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/xawt/libmawt.so
7f2a5ad87000-7f2a5ad92000 rwxp 00040000 07:00 375412                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/xawt/libmawt.so
7f2a5ad92000-7f2a5ad93000 rwxp 7f2a5ad92000 00:00 0 
7f2a5ad93000-7f2a5ae1d000 r-xp 00000000 07:00 375454                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libawt.so
7f2a5ae1d000-7f2a5af1c000 ---p 0008a000 07:00 375454                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libawt.so
7f2a5af1c000-7f2a5af35000 rwxp 00089000 07:00 375454                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libawt.so
7f2a5af35000-7f2a5af59000 rwxp 7f2a5af35000 00:00 0 
7f2a5af59000-7f2a5af60000 r-xs 00000000 07:00 84071                      /usr/lib/gconv/gconv-modules.cache
7f2a5af60000-7f2a5af9f000 r-xp 00000000 07:00 114213                     /usr/lib/locale/en_AU.utf8/LC_CTYPE
7f2a5af9f000-7f2a5b034000 rwxp 7f2a5af9f000 00:00 0 
7f2a5b034000-7f2a5b1bf000 r-xs 02df0000 07:00 375487                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/rt.jar
7f2a5b1bf000-7f2a5b1f2000 rwxp 7f2a5b1bf000 00:00 0 
7f2a5b1f2000-7f2a5b211000 rwxp 7f2a5b1f2000 00:00 0 
7f2a5b211000-7f2a5b21c000 rwxp 7f2a5b211000 00:00 0 
7f2a5b21c000-7f2a5b2b9000 rwxp 7f2a5b21c000 00:00 0 
7f2a5b2b9000-7f2a5b2c4000 rwxp 7f2a5b2b9000 00:00 0 
7f2a5b2c4000-7f2a5b2e3000 rwxp 7f2a5b2c4000 00:00 0 
7f2a5b2e3000-7f2a5b2ee000 rwxp 7f2a5b2e3000 00:00 0 
7f2a5b2ee000-7f2a5b38b000 rwxp 7f2a5b2ee000 00:00 0 
7f2a5b38b000-7f2a5b391000 rwxp 7f2a5b38b000 00:00 0 
7f2a5b391000-7f2a5b3df000 rwxp 7f2a5b391000 00:00 0 
7f2a5b3df000-7f2a5c8a0000 rwxp 7f2a5b3df000 00:00 0 
7f2a5c8a0000-7f2a607e0000 rwxp 7f2a5c8a0000 00:00 0 
7f2a607e0000-7f2a61ce0000 rwxp 7f2a607e0000 00:00 0 
7f2a61ce0000-7f2a757e0000 rwxp 7f2a61ce0000 00:00 0 
7f2a757e0000-7f2a76260000 rwxp 7f2a757e0000 00:00 0 
7f2a76260000-7f2a7ffe0000 rwxp 7f2a76260000 00:00 0 
7f2a7ffe0000-7f2a7ffe3000 rwxp 7f2a7ffe0000 00:00 0 
7f2a7ffe3000-7f2a7ffe6000 r-xs 00000000 07:00 181652                     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
7f2a7ffe6000-7f2a7ffef000 r-xs 00000000 07:00 181647                     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
7f2a7ffef000-7f2a8025f000 rwxp 7f2a7ffef000 00:00 0 
7f2a8025f000-7f2a82fef000 rwxp 7f2a8025f000 00:00 0 
7f2a82fef000-7f2a82ffd000 r-xp 00000000 07:00 375424                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libzip.so
7f2a82ffd000-7f2a830ff000 ---p 0000e000 07:00 375424                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libzip.so
7f2a830ff000-7f2a83102000 rwxp 00010000 07:00 375424                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libzip.so
7f2a83102000-7f2a83103000 rwxp 7f2a83102000 00:00 0 
7f2a83103000-7f2a8312b000 r-xp 00000000 07:00 375437                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libjava.so
7f2a8312b000-7f2a8322b000 ---p 00028000 07:00 375437                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libjava.so
7f2a8322b000-7f2a83232000 rwxp 00028000 07:00 375437                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libjava.so
7f2a83232000-7f2a8323f000 r-xp 00000000 07:00 375419                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libverify.so
7f2a8323f000-7f2a8333e000 ---p 0000d000 07:00 375419                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libverify.so
7f2a8333e000-7f2a83341000 rwxp 0000c000 07:00 375419                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/libverify.so
7f2a83341000-7f2a8334b000 r-xp 00000000 07:00 137720                     /lib/libnss_files-2.7.so
7f2a8334b000-7f2a8354b000 ---p 0000a000 07:00 137720                     /lib/libnss_files-2.7.so
7f2a8354b000-7f2a8354d000 rwxp 0000a000 07:00 137720                     /lib/libnss_files-2.7.so
7f2a8354d000-7f2a83557000 r-xp 00000000 07:00 137730                     /lib/libnss_nis-2.7.so
7f2a83557000-7f2a83756000 ---p 0000a000 07:00 137730                     /lib/libnss_nis-2.7.so
7f2a83756000-7f2a83758000 rwxp 00009000 07:00 137730                     /lib/libnss_nis-2.7.so
7f2a83758000-7f2a83760000 r-xp 00000000 07:00 137716                     /lib/libnss_compat-2.7.so
7f2a83760000-7f2a8395f000 ---p 00008000 07:00 137716                     /lib/libnss_compat-2.7.so
7f2a8395f000-7f2a83961000 rwxp 00007000 07:00 137716                     /lib/libnss_compat-2.7.so
7f2a83961000-7f2a83977000 r-xp 00000000 07:00 137714                     /lib/libnsl-2.7.so
7f2a83977000-7f2a83b76000 ---p 00016000 07:00 137714                     /lib/libnsl-2.7.so
7f2a83b76000-7f2a83b78000 rwxp 00015000 07:00 137714                     /lib/libnsl-2.7.so
7f2a83b78000-7f2a83b7a000 rwxp 7f2a83b78000 00:00 0 
7f2a83b7a000-7f2a83b81000 r-xp 00000000 07:00 375426                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/native_threads/libhpi.so
7f2a83b81000-7f2a83c82000 ---p 00007000 07:00 375426                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/native_threads/libhpi.so
7f2a83c82000-7f2a83c84000 rwxp 00008000 07:00 375426                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/native_threads/libhpi.so
7f2a83c84000-7f2a83c85000 rwxp 7f2a83c84000 00:00 0 
7f2a83c85000-7f2a83c8d000 r-xp 00000000 07:00 137754                     /lib/librt-2.7.so
7f2a83c8d000-7f2a83e8c000 ---p 00008000 07:00 137754                     /lib/librt-2.7.so
7f2a83e8c000-7f2a83e8e000 rwxp 00007000 07:00 137754                     /lib/librt-2.7.so
7f2a83e8e000-7f2a83f0e000 r-xp 00000000 07:00 137707                     /lib/libm-2.7.so
7f2a83f0e000-7f2a8410d000 ---p 00080000 07:00 137707                     /lib/libm-2.7.so
7f2a8410d000-7f2a8410f000 rwxp 0007f000 07:00 137707                     /lib/libm-2.7.so
7f2a8410f000-7f2a84804000 r-xp 00000000 07:00 375443                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/server/libjvm.so
7f2a84804000-7f2a84903000 ---p 006f5000 07:00 375443                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/server/libjvm.so
7f2a84903000-7f2a84a4d000 rwxp 006f4000 07:00 375443                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/server/libjvm.so
7f2a84a4d000-7f2a84a8a000 rwxp 7f2a84a4d000 00:00 0 
7f2a84a8a000-7f2a84be2000 r-xp 00000000 07:00 137670                     /lib/libc-2.7.so
7f2a84be2000-7f2a84de2000 ---p 00158000 07:00 137670                     /lib/libc-2.7.so
7f2a84de2000-7f2a84de5000 r-xp 00158000 07:00 137670                     /lib/libc-2.7.so
7f2a84de5000-7f2a84de7000 rwxp 0015b000 07:00 137670                     /lib/libc-2.7.so
7f2a84de7000-7f2a84dec000 rwxp 7f2a84de7000 00:00 0 
7f2a84dec000-7f2a84dee000 r-xp 00000000 07:00 137687                     /lib/libdl-2.7.so
7f2a84dee000-7f2a84fee000 ---p 00002000 07:00 137687                     /lib/libdl-2.7.so
7f2a84fee000-7f2a84ff0000 rwxp 00002000 07:00 137687                     /lib/libdl-2.7.so
7f2a84ff0000-7f2a85006000 r-xp 00000000 07:00 137748                     /lib/libpthread-2.7.so
7f2a85006000-7f2a85206000 ---p 00016000 07:00 137748                     /lib/libpthread-2.7.so
7f2a85206000-7f2a85208000 rwxp 00016000 07:00 137748                     /lib/libpthread-2.7.so
7f2a85208000-7f2a8520c000 rwxp 7f2a85208000 00:00 0 
7f2a8520c000-7f2a85229000 r-xp 00000000 07:00 137650                     /lib/ld-2.7.so
7f2a85229000-7f2a8522b000 rwxp 7f2a85229000 00:00 0 
7f2a8522b000-7f2a8522c000 r-xs 00000000 07:00 181644                     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
7f2a8522c000-7f2a8522d000 r-xs 00000000 07:00 181637                     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
7f2a8522d000-7f2a8522e000 r-xs 00000000 07:00 181635                     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
7f2a8522e000-7f2a85235000 r-xs 00000000 07:00 181631                     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
7f2a85235000-7f2a8523c000 r-xs 00110000 07:00 375469                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/resources.jar
7f2a8523c000-7f2a85248000 r-xs 0010f000 07:00 421212                     /home/furuno/.netbeans/6.1/jogl-runtime/jogl.jar
7f2a85248000-7f2a85252000 rwxp 7f2a85248000 00:00 0 
7f2a85252000-7f2a85308000 rwxp 7f2a85252000 00:00 0 
7f2a85308000-7f2a8530a000 rwxp 7f2a85308000 00:00 0 
7f2a8530a000-7f2a85311000 r-xp 00000000 07:00 375410                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/jli/libjli.so
7f2a85311000-7f2a85412000 ---p 00007000 07:00 375410                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/jli/libjli.so
7f2a85412000-7f2a85414000 rwxp 00008000 07:00 375410                     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/jli/libjli.so
7f2a85414000-7f2a85415000 rwxp 7f2a85414000 00:00 0 
7f2a85415000-7f2a85418000 r-xs 00000000 07:00 181650                     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
7f2a85418000-7f2a8541a000 r-xs 00000000 07:00 180229                     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
7f2a8541a000-7f2a8541c000 r-xs 00004000 07:00 421255                     /home/furuno/.netbeans/6.1/gluegen-runtime/gluegen-rt.jar
7f2a8541c000-7f2a85424000 rwxs 00000000 07:00 510100                     /tmp/hsperfdata_furuno/5948
7f2a85424000-7f2a85425000 rwxp 7f2a85424000 00:00 0 
7f2a85425000-7f2a85426000 r-xp 7f2a85425000 00:00 0 
7f2a85426000-7f2a85429000 rwxp 7f2a85426000 00:00 0 
7f2a85429000-7f2a8542b000 rwxp 0001d000 07:00 137650                     /lib/ld-2.7.so
7fff8d416000-7fff8d42b000 rwxp 7ffffffea000 00:00 0                      [stack]
7fff8d5fe000-7fff8d600000 r-xp 7fff8d5fe000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

VM Arguments:
jvm_args: -Djava.library.path=/home/furuno/.netbeans/6.1/jogl-runtime/jogl.jar-natives-linux-amd64:/home/furuno/.netbeans/6.1/gluegen-runtime/gluegen-rt.jar-natives-linux-amd64 
java_command: org.yourorghere.SimpleJOGL
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=furuno
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64/server:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/amd64:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/../lib/amd64
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x6616e0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x6616e0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x5044d0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x5044d0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x5044d0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x5044d0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x506740], sa_mask[0]=0x00000004, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x5064a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGTERM: [libjvm.so+0x5064a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x5064a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64
libc:glibc 2.7 NPTL 2.7 
rlimit: STACK 8192k, CORE 0k, NPROC 16383, NOFILE 1024, AS infinity
load average:2.10 0.85 0.31

CPU:total 2 (2 cores per cpu, 1 threads per core) family 15 model 107 stepping 1, cmov, cx8, fxsr, mmx, sse, sse2, sse3, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 2063204k(64276k free), swap 976552k(976552k free)

vm_info: Java HotSpot(TM) 64-Bit Server VM (10.0-b22) for linux-amd64 JRE (1.6.0_06-b02), built on Mar 25 2008 01:03:02 by "java_re" with gcc 3.2.2 (SuSE Linux)

time: Sun Aug 17 07:39:54 2008
elapsed time: 1 seconds

```I'm using the Sun's JRE & JDK (JDK 6 update 6) with NetBeans IDE 6.1 and NetBeans OpenGL Pack. What can I possibly do to resolve this problem ? :confused:

Thanks in advance.

---

### Post by HotCupOfJava on 2008-08-15
We might have to take a peek at your Java code to get to the bottom of this.....

Perhaps a moderator/admin could move this thread to "programming talk" too...

I don't suppose there is a way we could peek at your code?

---

### Post by furuno on 2008-08-15
Well, the code is not the problem here, *All* OpenGL program gets that error message so I don't think the code is the problem, since that any of my OpenGL program runs well on my Windows system with the same environment (JDK 6 update 6, NetBeans 6.1, and NB OpenGL Pack). So I figure out that the problem is within either the my JVM/NetBeans/Ubuntu setup.

Btw, the code is a simple JOGL application used in many open GL tutorial...

---

### Post by HotCupOfJava on 2008-08-15
Ah, I see. Have you tried installing any packages to increase compatibility with OpenGL? There are some libraries and extensions available that may help. Open Synaptic Package Manager and search "OpenGL". You will find a lengthy list of packages, many of which are related to rendering. The descriptions tell you what they do. 

I will go ahead and concede that you may already know about all of this, though - in which case I am out of my league.

---

### Post by fx3 on 2008-11-11
> **furuno said:**
> Well, the code is not the problem here, *All* OpenGL program gets that error message so I don't think the code is the problem, since that any of my OpenGL program runs well on my Windows system with the same environment (JDK 6 update 6, NetBeans 6.1, and NB OpenGL Pack). So I figure out that the problem is within either the my JVM/NetBeans/Ubuntu setup.

I bet you have an ATI-card, right?!

---

