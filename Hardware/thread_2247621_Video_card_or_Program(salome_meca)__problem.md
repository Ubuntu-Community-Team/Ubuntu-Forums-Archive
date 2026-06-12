---
title: "Video card or Program(salome meca)  problem"
date: 2014-10-09
forum: Hardware
---

### Post by mihe on 2014-10-09
I am trying to understand poor graphical performance when using a cad program (salome meca). I do not know if it is related to video card or the program.

The computer is new with:
Video card: nvidia Quadro K2000
OS Ubuntu 14.04 + Xubuntu
Program Salome meca 2012.2

Prior to installing Ubuntu the machine had following spec:
Operativsystem:    Windows 7 Professional, 64-bit (Service Pack 1)
DirectX-version:    11.0
GPU-enhetens processor:        Quadro K2000
Drivrutinsversion:    331.82
Direct3D API-version:    11
Direct3D funktionsniv?:    11_0
CUDA-k?rnor:        384
K?rnklocka:        954 MHz
Minnesdatahastighet:    4000 MHz
Minnesgr?nssnitt:    128 Bitar
Minnesbandbredd:    64.00 GB/s
Totalt tillg?ngligt grafikminne:    9956 MB
Dedicerat videominne:    2048 MB GDDR5
Systemvideominne:    0 MB
Delat systemminne:    7908 MB
Video BIOS-version:    80.07.C7.00.08

According to nvidia.com I should used video card driver 340.46 for linux.
Ubuntu detects 3 Additional drivers that can be used; nouveau, nvidia 331.38 , and nvidia 331.38 updated.

I did not want to try to install 331.82 or 340.46 directly. I see a lot of things can go wrong on different forums... I therefore started testing the three already available options. I have listed the three test I made below. From my experience working with this size of FE model should not be a problem(500000nodes and 260000 tetra10 elements). Experience = abaqus/catia experience from other windows/linux systems about 10years ago... 

My questions:
-When using  nouveau driver is the nvidia card used at all(newbie question I know)?
-Should not nvidia driver perform better than nouveau?
-Can you suggest a way to test the video card performance? Is there some performance test program one can use?

BR/Micke

####################################################
First test  nvidia 331.38 updated
Salome not working ok, lagging when rotating or zooming(visually I would say about 0.5 second per frame), for model with 500000nodes and 260000 tetra10 elements.
Salome uses ~2GB ram, one CPU varying from 0-100.

lspci -vnn | grep -i VGA -A 12
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107GL [Quadro K2000] [10de:0ffe] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device [10de:094c]
    Flags: bus master, fast devsel, latency 0, IRQ 82
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at fb000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

02:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:094c]

glxinfo | grep OpenGL | grep renderer
OpenGL renderer string: Quadro K2000/PCIe/SSE2

lsmod | grep nvidia
nvidia              10675249  66
drm                   303102  3 nvidia

glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
303 frames in 5.0 seconds = 60.400 FPS
300 frames in 5.0 seconds = 59.952 FPS
300 frames in 5.0 seconds = 59.952 FPS
Without sync to Black option I get ~12500FPS.

####################################################
Second test  nouveau:
Salome working ok, but not impressive, some lagging(visually I would say about <0.1 second per frame).
Salome uses ~1GB ram.

lspci -vnn | grep -i VGA -A 12
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107GL [Quadro K2000] [10de:0ffe] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device [10de:094c]
    Flags: bus master, fast devsel, latency 0, IRQ 82
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at fb000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau

02:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:094c]

glxinfo | grep OpenGL | grep renderer
OpenGL renderer string: Gallium 0.4 on NVE7

lsmod | grep nvidia


glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
602 frames in 5.0 seconds = 120.291 FPS
600 frames in 5.0 seconds = 119.902 FPS
600 frames in 5.0 seconds = 119.903 FPS

####################################################
Third test  nvidia 331.38
Salome not working ok, lagging when rotating or zooming(visually I would say about 0.5 second per frame).
Salome uses ~2GB ram, one CPU varying from 0-100.

lspci -vnn | grep -i VGA -A 12
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107GL [Quadro K2000] [10de:0ffe] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device [10de:094c]
    Flags: bus master, fast devsel, latency 0, IRQ 82
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at fb000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

02:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:094c]

glxinfo | grep OpenGL | grep renderer
OpenGL renderer string: Quadro K2000/PCIe/SSE2

lsmod | grep nvidia
nvidia              10675249  56
drm                   303102  3 nvidia

glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
303 frames in 5.0 seconds = 60.479 FPS
300 frames in 5.0 seconds = 59.982 FPS
300 frames in 5.0 seconds = 59.982 FPS

BR/Micke

---

### Post by mihe on 2014-10-15
I tried command nvidia-smi while working(rotation the model) in salome post-pro:

nvidia-smi -l 1

+------------------------------------------------------+                       
| NVIDIA-SMI 331.38     Driver Version: 331.38         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+=====================neutral
|   0  Quadro K2000        Off  | 0000:02:00.0      On |                  N/A |
| 30%   34C    P8    N/A /  N/A |    427MiB /  2047MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|============================================================================neutral
|  No running compute processes found                                         |

It seem the GPU is zero and memory usage is 427 out of 2047MiB.
-Why is GPU zero?.
-Would be interesting to see similar print out from somebody here on the forum with nvidia video card and nvidia driver!
/Micke

---

### Post by mihe on 2014-10-15
Please, can someone Comment on if gpu=0 is a resonable value or if it indicates that something is wrong.

---

