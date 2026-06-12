---
title: "IGP 760G using radeon driver load amdgpu module ... need avoid it ?"
date: 2022-11-23
forum: Hardware
---

### Post by aug7744 on 2022-11-23
Hello.
Thanks very much for reading my topic.
IGP 760G Radeon HD 3000. An IGP before of 2010. Have enough processing for videos and few current softwares.
In installed Lubuntu 20.04.5 had happened strange issues in few softwares when trying use OpenGL 3.3 being few graphics errors , error closing software and x11 crash at point not any image is rendered in screen.
Thus I had done the command below

lspci -k | grep -A 3 -E "(VGA|3D)"

01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000]
        Subsystem: Biostar Microtech Int'l Corp RS780L [Radeon 3000]
        Kernel driver in use: radeon
        Kernel modules: radeon, amdgpu
        
Is correct load amdgpu module even if is used the radeon driver ? amdgpu module is for new video cards.
I want test disabling load amdgpu module in OS startup for see if not happen more any problems.

Also I had forced enabled OpenGL 3.3 because was available only OpenGL 3.0.
IGP is OpenGL 3.3.

sudo nano /etc/environment
MESA_GL_VERSION_OVERRIDE=3.3
MESA_GLSL_VERSION_OVERRIDE=330

and created
sudo nano /etc/X11/xorg.conf.d/20-radeon.conf
Section "Device"
    Identifier  "Radeon"
    Driver "radeon"
    Option "AccelMethod" "glamor"
    Option "DRI" "3"
    Option "TearFree" "on"
    Option "ColorTiling" "on"
    Option "ColorTiling2D" "on"
    Option "ShadowPrimary" "off"
    Option "EXAVSync" "no"
EndSection

Not any fixes.
I not have information if the IGP is fully OpenGL 3.3. Thus need test and also if using DRI2 fix the issue.
I only want optimize settings and not run softwares not being compatible with Radeon HD 3000.

When doing kernel update is showed several missing firmware files

W: Possible missing firmware /lib/firmware/amdgpu/ip_discovery.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_7_ta.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_7_sos.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_0_ta.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_0_sos.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_8_ta.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_8_toc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_5_ta.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_5_toc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/aldebaran_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_4_ta.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/psp_13_0_4_toc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_7_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_7_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_7_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_7_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_7_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_7_ce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_6_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_6_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_6_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_6_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_6_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_10_3_6_ce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_2_imu.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_imu.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_imu.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_2_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_2_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_2_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_2_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_toc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sdma_5_2_7.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sdma_5_2_6.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sdma_6_0_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sdma_6_0_1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sdma_6_0_0.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi10_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_2_mes1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_2_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_mes1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_mes1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vcn_4_0_4.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vcn_4_0_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vcn_4_0_0.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vcn_3_1_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/smu_13_0_7.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/smu_13_0_0.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/dcn_3_2_1_dmcub.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/dcn_3_2_0_dmcub.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/dcn_3_1_6_dmcub.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/dcn_3_1_5_dmcub.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/dcn_3_1_4_dmcub.bin for module amdgpu

Any problem if not find firmware when updating the kernel ?

IGP Radeon 3000 HD has powerplay (power management).
However using monitoring tools the clock is always 350 MHZ in idle.
I not understand if oowerplay is enabled or if BIOS not allow changing power mode for IGP.

Thanks for reply.

---

