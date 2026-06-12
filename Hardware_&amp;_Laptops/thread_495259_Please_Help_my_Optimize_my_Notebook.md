---
title: "Please Help my Optimize my Notebook"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by fragility14 on 2007-07-07
i am using a centrino 1,5 notebook with 1024 DDR333 ram and an Intel 855GM Video Card and an 82801 Chipset.

I have had trouble getting help with specific issues, and I think it would be expedient to run a series of diagnostics with someone and then post the results I get.

Problems: Sound crackles and videos skip erratically especially if system resources are being used. The system seems to use a whole lot of its processor power using a program like Amarok (90%) and will stall because of it but will only be using a quarter of its ram. Also, I tried to install the synaptics touchpad program and it doesn't work. It says I need to set something to "true" in xorg.conf, which i can't access because it says there is no such program. Also, on the command line it stalls for a while when I open it before showing my computer/username.

i realize that is a mess of things, but it seems that  the same sort of analysis could solve all problems, because as far as I now all of this hardware should work (though, all the problems I initially had turned out to be a bad hard drive which has been switched out, though I got it out of an old computer, so would be interested in running an integrity check on it if nothing else pans out.)




Just give me commands and I will copy and paste the results :D



Here's my glxinfo since it is something i know how to give you.

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by fredj on 2007-07-07
Open a terminal (Applications - Accessories - terminal).
Change to the xorg directory 'cd /etc/X11'
Use ls to list the files, among them you should see xorg.conf (this is a text file)
Make a backup copy of it 'sudo cp xorg.conf xorg.conf.save'.
You can then change the file using 'sudo gedit xorg.conf'
Use the ls command again to check that the backup file is there.
Be VERY VERY carefull. Changing the xorg.conf file recklessly can stop your GUI from working. 
If something goes wrong use the copy command to restore the xorg.conf file from the backup copy.

---

### Post by fredj on 2007-07-07
With regard to the other problems, I wouldn't expect things to be so slow although a centrino 1.5 isn't the
fastest of processors. Don't worry about the RAM use, linux uses far less memory than windows.
Did your system check the hard disk drive when you first booted into Linux.
Go into the bios (usually by holding down the F2 or Delete keys) when powering up. See if the hard disk
is recognised properly.

---

### Post by fragility14 on 2007-07-07
the hard disk is recognized properly.

I used this computer for music and tv shows ALL THE TIME on windows, it has the hardware to do it. 

An example of what the sound is doing:

In Battle for Wesnoth on the start screen it the sound is fine, but if I put my cursor over anything, the sound remains crackelly as long as my cursor is over the menu option.

edit: and seriously when i open the terminal it sits there blinking for like a minute before showing my computer name/sign in


I'd also like to mention that I am not against going through the formatting process yet again, if there is some coherent order of operations to getting everything working well which I should be aware of.

---

### Post by fragility14 on 2007-07-07
the command CD isnt found and there is no such file as x11


when i actually go to etc/x11 in the GUI i am able to open xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by fragility14 on 2007-07-08
guys I really need help. My sound doesn't work consistently and I cant figure out whats wrong (because yesterday it kept playing while the system was freezing.


My programs lock up A LOT. Specifically any web browser, but I guess because that is what I use. 

I found out how to fix the touchpad problem from xorg.conf but gedit /etc/x11/conf or whatever the file is comes up blank with the gedit command.

I am VERY willing to reformat this damn computer again, it is simply that I suspect if I do it I will come back with the same problem.

I switched my sound type to ALSA instead of auto, I was able to listen to a whole podcast yesterday essentially without problems, it isnt particularly a problem I can replicate, outsde of to say that it happens more when a system sort of application (add remove programs) is open.


I could really use help and dont particularly know who to ask, i have had horrible luck getting any help on these forms when i use google people generally seem to have different problems, such as this sound card simply not working. The thing is it can make clear sound, it just often chooses not to, I dont have external speakers handy but am going to try some out just to make sure it isnt the speakers themselves, but I strongly doubt that being as it only does it sometimes.

It also can't really play videos smoothly (as I've said on windows I used to watch tv shows on this computer all the time.)

edit: here is my dmesg

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f6d0000 end: 000000003f7d0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f7d0000 size: 000000000000f000 end: 000000003f7df000 type: 3
[    0.000000] copy_e820_map() start: 000000003f7df000 size: 0000000000021000 end: 000000003f800000 type: 4
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7d0000 - 000000003f7df000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7df000 - 000000003f800000 (ACPI NVS)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 260048) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   260048
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   260048
[    0.000000] On node 0 totalpages: 260048
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 239 pages used for memmap
[    0.000000]   HighMem zone: 30433 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f63b0
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x07000415 MSFT 0x00000097) @ 0x3f7d0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x07000415 MSFT 0x00000097) @ 0x3f7d0200
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x07000415 MSFT 0x00000097) @ 0x3f7df040
[    0.000000] ACPI: SSDT (v001    AMI   CPU1PM 0x00000001 INTL 0x02002026) @ 0x3f7d3b70
[    0.000000] ACPI: DSDT (v001  1ABWG 1ABWG001 0x00000001 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:c0800000)
[    0.000000] Detected 1500.080 MHz processor.
[    7.248703] Built 1 zonelists.  Total pages: 258017
[    7.248709] Kernel command line: root=UUID=a0da214b-8dcf-45cd-b710-3340596efb5a ro quiet splash
[    7.248896] Found and enabled local APIC!
[    7.248899] mapped APIC to ffffd000 (fee00000)
[    7.248903] Enabling fast FPU save and restore... done.
[    7.248907] Enabling unmasked SIMD FPU exception support... done.
[    7.248917] Initializing CPU#0
[    7.248993] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    7.250469] Console: colour VGA+ 80x25
[    7.250881] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    7.251377] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.288114] Memory: 1019992k/1040192k available (1992k kernel code, 19392k reserved, 900k data, 328k init, 122688k highmem)
[    7.288125] virtual kernel memory layout:
[    7.288127]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    7.288128]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.288130]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    7.288131]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    7.288132]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    7.288134]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    7.288135]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    7.288139] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.364895] Calibrating delay using timer specific routine.. 3002.11 BogoMIPS (lpj=6004239)
[    7.364939] Security Framework v1.0.0 initialized
[    7.364946] SELinux:  Disabled at boot.
[    7.364964] Mount-cache hash table entries: 512
[    7.365108] CPU: After generic identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[    7.365120] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.365123] CPU: L2 cache: 2048K
[    7.365126] CPU: After all inits, caps: afe9fbbf 00000000 00000000 00002040 00000180 00000000 00000000
[    7.365136] Compat vDSO mapped to ffffe000.
[    7.365140] Remapping vsyscall page to ffffe000
[    7.365151] Checking 'hlt' instruction... OK.
[    7.380982] SMP alternatives: switching to UP code
[    7.381188] Freeing SMP alternatives: 11k freed
[    7.381383] Early unpacking initramfs... done
[    7.861655] ACPI: Core revision 20060707
[    7.862488] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    7.867524] ACPI: setting ELCR to 0200 (from 0e28)
[    7.951388] CPU0: Intel(R) Pentium(R) M processor 1.50GHz stepping 06
[    7.951394] SMP motherboard not detected.
[    8.056326] Brought up 1 CPUs
[    8.056581] Booting paravirtualized kernel on bare hardware
[    8.056648] Time: 18:07:34  Date: 06/07/107
[    8.056677] NET: Registered protocol family 16
[    8.056761] EISA bus registered
[    8.056765] ACPI: bus type pci registered
[    8.057890] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    8.057892] PCI: Using configuration type 1
[    8.057894] Setting up standard PCI resources
[    8.069970] ACPI: Interpreter enabled
[    8.069973] ACPI: Using PIC for interrupt routing
[    8.070340] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.070346] PCI: Probing PCI hardware (bus 00)
[    8.070714] Boot video device is 0000:00:02.0
[    8.071004] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    8.071008] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[    8.071376] PCI: Transparent bridge - 0000:00:1e.0
[    8.071428] PCI: Bus #02 (-#05) is hidden behind transparent bridge #01 (-#01) (try 'pci=assign-busses')
[    8.071431] Please report the result to linux-kernel to fix this permanently
[    8.071447] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.099456] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    8.111998] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    8.112410] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    8.112811] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    8.113208] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    8.113605] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.114002] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.114401] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.114800] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    8.114962] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.114971] pnp: PnP ACPI init
[    8.122371] pnp: PnP ACPI: found 10 devices
[    8.122375] PnPBIOS: Disabled by ACPI PNP
[    8.122412] PCI: Using ACPI for IRQ routing
[    8.122415] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.126141] NET: Registered protocol family 8
[    8.126144] NET: Registered protocol family 20
[    8.127147] pnp: 00:08: ioport range 0x1100-0x113f has been reserved
[    8.127150] pnp: 00:08: ioport range 0x1254-0x1254 has been reserved
[    8.127153] pnp: 00:08: ioport range 0x12d4-0x12d4 has been reserved
[    8.127157] pnp: 00:08: ioport range 0x1300-0x1375 has been reserved
[    8.127160] pnp: 00:08: ioport range 0x1377-0x137f has been reserved
[    8.127417] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    8.127431] PCI: Bus 2, cardbus bridge: 0000:01:03.0
[    8.127433]   IO window: 0000c000-0000c0ff
[    8.127437]   IO window: 0000c400-0000c4ff
[    8.127442]   PREFETCH window: 40000000-43ffffff
[    8.127446]   MEM window: 48000000-4bffffff
[    8.127450] PCI: Bridge: 0000:00:1e.0
[    8.127453]   IO window: c000-cfff
[    8.127458]   MEM window: ffb00000-ffbfffff
[    8.127462]   PREFETCH window: 40000000-43ffffff
[    8.127475] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.127759] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 3
[    8.127762] PCI: setting IRQ 3 as level-triggered
[    8.127766] ACPI: PCI Interrupt 0000:01:03.0[A] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[    8.127773] PCI: Setting latency timer of device 0000:01:03.0 to 64
[    8.127795] NET: Registered protocol family 2
[    8.164241] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.164358] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.165263] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.165855] TCP: Hash tables configured (established 131072 bind 65536)
[    8.165860] TCP reno registered
[    8.176349] checking if image is initramfs... it is
[    9.013755] Freeing initrd memory: 6765k freed
[    9.014229] audit: initializing netlink socket (disabled)
[    9.014245] audit(1183831654.764:1): initialized
[    9.014328] highmem bounce pool size: 64 pages
[    9.014398] VFS: Disk quotas dquot_6.5.1
[    9.014421] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.014478] io scheduler noop registered
[    9.014481] io scheduler anticipatory registered
[    9.014483] io scheduler deadline registered
[    9.014494] io scheduler cfq registered (default)
[    9.014816] isapnp: Scanning for PnP cards...
[    9.368293] isapnp: No Plug & Play device found
[    9.394031] Real Time Clock Driver v1.12ac
[    9.394090] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.394770] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[    9.394781] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    9.394861] mice: PS/2 mouse device common for all mice
[    9.395488] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.395742] input: Macintosh mouse button emulation as /class/input/input0
[    9.395777] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.395781] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.396001] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.401236] i8042.c: Detected active multiplexing controller, rev 1.0.
[    9.402139] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.402144] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.402147] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.402150] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.402153] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.402272] EISA: Probing bus 0 at eisa.0
[    9.402324] EISA: Detected 0 cards.
[    9.432409] TCP cubic registered
[    9.432418] NET: Registered protocol family 1
[    9.432476] Testing NMI watchdog ... OK.
[    9.472153] Using IPI No-Shortcut mode
[    9.472209] ACPI: (supports S0 S3 S4 S5)
[    9.472257]   Magic number: 15:504:139
[    9.472589] Freeing unused kernel memory: 328k freed
[    9.473248] input: AT Translated Set 2 keyboard as /class/input/input1
[    9.475028] Time: tsc clocksource has been installed.
[   41.633399] Capability LSM initialized
[   44.856636] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   44.856642] ACPI: Processor [CPU1] (supports 8 throttling states)
[   44.861940] ACPI: Thermal Zone [THRM] (11 C)
[   78.579918] usbcore: registered new interface driver usbfs
[   78.579942] usbcore: registered new interface driver hub
[   78.579962] usbcore: registered new device driver usb
[   78.585818] USB Universal Host Controller Interface driver v3.0
[   78.586206] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   78.586209] PCI: setting IRQ 11 as level-triggered
[   78.586214] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   78.586226] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   78.586230] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   78.586401] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   78.586425] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000e480
[   78.586535] usb usb1: configuration #1 chosen from 1 choice
[   78.586563] hub 1-0:1.0: USB hub found
[   78.586569] hub 1-0:1.0: 2 ports detected
[   78.697294] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[   78.697297] PCI: setting IRQ 5 as level-triggered
[   78.697301] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   78.697310] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   78.697314] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   78.697334] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   78.697355] uhci_hcd 0000:00:1d.1: irq 5, io base 0x0000e800
[   78.697439] usb usb2: configuration #1 chosen from 1 choice
[   78.697466] hub 2-0:1.0: USB hub found
[   78.697472] hub 2-0:1.0: 2 ports detected
[   78.811569] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   78.811572] PCI: setting IRQ 9 as level-triggered
[   78.811575] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   78.811583] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   78.811587] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   78.811606] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   78.811625] uhci_hcd 0000:00:1d.2: irq 9, io base 0x0000e880
[   78.811709] usb usb3: configuration #1 chosen from 1 choice
[   78.811735] hub 3-0:1.0: USB hub found
[   78.811744] hub 3-0:1.0: 2 ports detected
[   83.477202] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   83.477207] PCI: setting IRQ 10 as level-triggered
[   83.477212] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   83.477225] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   83.477229] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   83.477261] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   83.477295] ehci_hcd 0000:00:1d.7: debug port 1
[   83.477301] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   83.477311] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xffdffc00
[   83.481564] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   83.481652] usb usb4: configuration #1 chosen from 1 choice
[   83.481678] hub 4-0:1.0: USB hub found
[   83.481684] hub 4-0:1.0: 6 ports detected
[   83.558540] SCSI subsystem initialized
[   83.574647] libata version 2.20 loaded.
[   86.131176] ata_piix 0000:00:1f.1: version 2.10ac1
[   86.131191] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   86.131200] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   86.131220] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   86.131266] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   86.131295] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   86.131319] scsi0 : ata_piix
[   86.310317] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   86.310322] ata1.00: ATA-6: TOSHIBA MK8026GAX, PA001G, max UDMA/100
[   86.310325] ata1.00: 156301488 sectors, multi 16: LBA 
[   86.319103] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   86.319107] ata1.00: configured for UDMA/100
[   86.319115] scsi1 : ata_piix
[   86.670648] ata2.00: ATAPI, max UDMA/33
[   86.850867] ata2.00: configured for UDMA/33
[   86.859489] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8026GA PA00 PQ: 0 ANSI: 5
[   86.860215] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SDW-431S   MSU1 PQ: 0 ANSI: 5
[  109.920224] ieee1394: Initialized config rom entry `ip1394'
[  109.930789] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[  112.755688] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[ffbfe800-ffbfefff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[  112.798556] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[  112.798585] 8139cp 0000:01:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[  112.798588] 8139cp 0000:01:0c.0: Try the "8139too" driver instead.
[  112.890962] 8139too Fast Ethernet driver 0.9.28
[  112.891004] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[  112.891317] eth0: RealTek RTL8139 at 0xf88c2400, 00:03:0d:13:dc:d3, IRQ 5
[  112.891320] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[  114.151537] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d492230222b]
[  120.262366] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[  120.262381] sda: Write Protect is off
[  120.262383] sda: Mode Sense: 00 3a 00 00
[  120.262397] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  120.262445] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[  120.262454] sda: Write Protect is off
[  120.262456] sda: Mode Sense: 00 3a 00 00
[  120.262470] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  120.262473]  sda: sda1 sda2
[  120.572948] sd 0:0:0:0: Attached scsi disk sda
[  121.966406] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  121.966426] sr 1:0:0:0: Attached scsi generic sg1 type 5
[  122.107337] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[  122.107342] Uniform CD-ROM driver Revision: 3.20
[  122.107390] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  125.885382] Attempting manual resume
[  125.885386] swsusp: Resume From Partition 8:2
[  125.885388] PM: Checking swsusp image.
[  125.885553] PM: Resume from disk failed.
[  113.744000] Time: acpi_pm clocksource has been installed.
[  113.768000] kjournald starting.  Commit interval 5 seconds
[  113.768000] EXT3-fs: mounted filesystem with ordered data mode.
[  183.492000] eth0: link down
[  186.312000] NET: Registered protocol family 17
[  186.948000] Linux agpgart interface v0.102 (c) Dave Jones
[  186.980000] agpgart: Detected an Intel 855 Chipset.
[  186.980000] agpgart: Detected 8060K stolen memory.
[  186.988000] agpgart: AGP aperture is 128M @ 0xf0000000
[  187.240000] intel_rng: FWH not detected
[  187.276000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  187.292000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  187.304000] iTCO_vendor_support: vendor-support=0
[  187.308000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  187.832000] ieee80211_crypt: registered algorithm 'NULL'
[  187.832000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  187.832000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  187.852000] Yenta: CardBus bridge found at 0000:01:03.0 [1584:3200]
[  187.852000] Yenta: adjusting diagnostic: 40 -> 60
[  187.852000] Yenta: Using CSCINT to route CSC interrupts to PCI
[  187.852000] Yenta: Routing CardBus interrupts to PCI
[  187.852000] Yenta TI: socket 0000:01:03.0, mfunc 0x000c1002, devctl 0x44
[  187.884000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[  187.884000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  187.888000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x926eb1, caps: 0x804719/0x0
[  187.932000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[  188.112000] Yenta: ISA IRQ mask 0x00d0, PCI irq 3
[  188.112000] Socket status: 30000006
[  188.112000] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[  188.112000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[  188.112000] cs: IO port probe 0xc000-0xcfff: clean.
[  188.112000] pcmcia: parent PCI bridge Memory window: 0xffb00000 - 0xffbfffff
[  188.112000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[  188.112000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[  188.112000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[  188.136000] psmouse.c: Failed to reset mouse on isa0060/serio3
[  188.276000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  188.284000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 3 (level, low) -> IRQ 3
[  188.284000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  188.636000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[  188.636000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[  188.636000] cs: IO port probe 0x820-0x8ff: excluding 0x860-0x867
[  188.636000] cs: IO port probe 0xc00-0xcf7: clean.
[  188.636000] cs: IO port probe 0xa00-0xaff: clean.
[  189.104000] intel8x0_measure_ac97_clock: measured 55498 usecs
[  189.104000] intel8x0: clocking to 48000
[  197.544000] input: PS/2 Generic Mouse as /class/input/input3
[  197.744000] psmouse.c: Failed to enable mouse on isa0060/serio3
[  197.744000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0460)
[  197.744000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  197.744000] input: PC Speaker as /class/input/input4
[  198.116000] fuse init (API version 7.8)
[  198.280000] lp: driver loaded but no devices found
[  198.424000] Adding 1975984k swap on /dev/disk/by-uuid/e87bfee9-c30c-41cb-8ae9-30117e1204c3.  Priority:-1 extents:1 across:1975984k
[  198.572000] EXT3 FS on sda1, internal journal
[  199.032000] NET: Registered protocol family 10
[  199.032000] lo: Disabled Privacy Extensions
[  199.032000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  207.792000] input: Power Button (FF) as /class/input/input5
[  207.796000] ACPI: Power Button (FF) [PWRF]
[  207.832000] input: Lid Switch as /class/input/input6
[  207.840000] ACPI: Lid Switch [LID]
[  207.884000] input: Sleep Button (CM) as /class/input/input7
[  207.888000] ACPI: Sleep Button (CM) [SLPB]
[  207.924000] input: Power Button (CM) as /class/input/input8
[  207.932000] ACPI: Power Button (CM) [PWRB]
[  207.952000] ACPI: AC Adapter [AC0] (on-line)
[  207.964000] Using specific hotkey driver
[  208.048000] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[  208.136000] ibm_acpi: ec object not found
[  208.180000] No dock devices found.
[  208.220000] ACPI: Battery Slot [BAT0] (battery present)
[  209.212000] pcc_acpi: loading...
[  209.240000] eth1: no IPv6 routers present
[  214.996000] ppdev: user-space parallel port driver
[  215.524000] [drm] Initialized drm 1.1.0 20060810
[  215.580000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  215.580000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[  215.580000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[  216.988000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  216.988000] apm: overridden by ACPI.
[  224.544000] Bluetooth: Core ver 2.11
[  224.544000] NET: Registered protocol family 31
[  224.544000] Bluetooth: HCI device and connection manager initialized
[  224.544000] Bluetooth: HCI socket layer initialized
[  224.680000] Bluetooth: L2CAP ver 2.8
[  224.680000] Bluetooth: L2CAP socket layer initialized
[  224.852000] Bluetooth: RFCOMM socket layer initialized
[  224.852000] Bluetooth: RFCOMM TTY layer initialized
[  224.852000] Bluetooth: RFCOMM ver 1.8
[  784.492000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  794.592000] eth1: no IPv6 routers present
[  807.184000] eth1: no IPv6 routers present

---

### Post by fragility14 on 2007-07-08
here are the results of lspci

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
01:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



edit: for some reason it shows multiple videocards/graphics controllers using both windows and linux, in windows I had the ones it wasnt actually using set to disabled, but if you uninstall both and restart it finds both of them at once....not a known slowdown caused by it.

---

### Post by fragility14 on 2007-07-09
I tried totally reformatting my computer and starting over to go from a rational install point, except now it is going even more slowly than before. Does anyone know how to test a toshiba hard drive? Apparently they dont release testing software, I need help with this issue, my computer is going unusably slow while refusing to use resources. PLEASE HELP ME.

---

