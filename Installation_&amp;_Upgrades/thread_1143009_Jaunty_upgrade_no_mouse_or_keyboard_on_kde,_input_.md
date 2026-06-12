---
title: "Jaunty upgrade: no mouse or keyboard on kde, input fine on terminal"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by stakh on 2009-04-29
I tried to update from Hardy to Jaunty, but have met some problems:

Initially during boot I was dumped to a shell without starting kde. Doing

```
sudo aptitude update
```
followed by
```
sudo aptitude -f install kde
```
solved the issue: I can now login and enter a kde session.

However, when kde launches, I'm unable to use the keyboard or the touchpad. It's weird since I could use the keyboard to log into the kde session. Also, I can press Alt-F2 and get a launch box, but I can't type anything in it.

If I switch to a shell (Ctrl-Alt-F1) I can access a terminal and type just fine (this is how I'm typing this message with w3m, as my laptop is my only computer at home).

Does anyone have any idea of what's preventing kde from getting keyboard or mouse input?

---

### Post by Monsieur Gonzalez on 2009-04-29
I had a similar problem, and, if I remember correctly, it had something to do with some packages(ppa-kubuntu-experimental, I think) I had activated in 8.10 to get KDE4.2.2. 

Whenever I tried to upgrade packages, there was some xorg-server being held. Had to go into aptitude an install some fonts packages (sorry, cannot remember which ones) and then upgraded the xorg-server packages.

You could also try to take a look at your xorg.conf file (located at /etc/X11).

Mine looks like this for keyboard 

 Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "kbd"
EndSection

Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
EndSection

---

### Post by stakh on 2009-04-29
I tried the modified xorg.conf version, but there was no difference. I guess I will need more precise instructions.

I have the feeling that the font issue is probably secondary?... Some chunks of kde or x.org must not be correctly installed, for whatever reason...

---

### Post by Monsieur Gonzalez on 2009-04-30
What's the output of 'sudo apt-get update' in your system? Any error messages?

---

### Post by stakh on 2009-04-30
> **Monsieur Gonzalez said:**
> What's the output of 'sudo apt-get update' in your system? Any error messages?

This is what I get:
```


Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-pt_PT
Ign http://security.ubuntu.com jaunty-security/restricted Translation-pt_PT
Ign http://security.ubuntu.com jaunty-security/universe Translation-pt_PT
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-pt_PT
Hit http://security.ubuntu.com jaunty-security Release
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://be.archive.ubuntu.com jaunty Release.gpg
Ign http://be.archive.ubuntu.com jaunty/main Translation-pt_PT
Ign http://be.archive.ubuntu.com jaunty/restricted Translation-pt_PT
Ign http://be.archive.ubuntu.com jaunty/universe Translation-pt_PT
Ign http://be.archive.ubuntu.com jaunty/multiverse Translation-pt_PT
Hit http://be.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://be.archive.ubuntu.com jaunty-updates/main Translation-pt_PT
Ign http://be.archive.ubuntu.com jaunty-updates/restricted Translation-pt_PT
Ign http://be.archive.ubuntu.com jaunty-updates/universe Translation-pt_PT
Ign http://be.archive.ubuntu.com jaunty-updates/multiverse Translation-pt_PT
Hit http://be.archive.ubuntu.com jaunty Release
Hit http://be.archive.ubuntu.com jaunty-updates Release
Hit http://be.archive.ubuntu.com jaunty/main Packages
Hit http://be.archive.ubuntu.com jaunty/restricted Packages
Hit http://be.archive.ubuntu.com jaunty/main Sources
Hit http://be.archive.ubuntu.com jaunty/restricted Sources
Hit http://be.archive.ubuntu.com jaunty/universe Packages
Hit http://be.archive.ubuntu.com jaunty/universe Sources
Hit http://be.archive.ubuntu.com jaunty/multiverse Packages
Hit http://be.archive.ubuntu.com jaunty/multiverse Sources
Hit http://be.archive.ubuntu.com jaunty-updates/main Packages
Hit http://be.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://be.archive.ubuntu.com jaunty-updates/main Sources
Hit http://be.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://be.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://be.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://be.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://be.archive.ubuntu.com jaunty-updates/multiverse Sources
A ler as listas de pacotes...

```
yep, that's portuguese

I guess many things are missing, but I don't know how to proceed

---

### Post by Monsieur Gonzalez on 2009-04-30
Can you try sudo apt-get install -f and sudo apt-get upgrade?

---

### Post by stakh on 2009-04-30
> **Monsieur Gonzalez said:**
> Can you try sudo apt-get install -f and sudo apt-get upgrade?

This is the output of sudo apt-get install -f

> 

A ler as listas de pacotes...
A construir árvore de dependências...
A ler a informação de estado...
Os seguintes pacotes foram instalados automaticamente e já não são necessários:
  espeak libg15render1 kwin libportaudio2 libxevie1 espeak-data libspeechd2
  libg15daemon-client1 libespeak1 libg15-1 speech-dispatcher libdotconf1.0
Utilize 'apt-get autoremove' para os remover.
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
2 pacotes não totalmente instalados ou removidos.
Após esta operação, serão utilizados 0B adicionais de espaço em disco.
A instalar mumble-server (1.1.7-3) ...
chmod: não consigo aceder a `/var/lib/mumble-server': Ficheiro ou directoria inexistente
dpkg: erro ao processar mumble-server (--configure):
 subprocesso post-installation script retornou erro do status de saída 1
dpkg: problemas com dependências impedem a configuração de mumble-server-web:
 mumble-server-web depende de mumble-server (>= 1.1.7-3); no entanto:
 O pacote mumble-server ainda não está configurado.
dpkg: erro ao processar mumble-server-web (--configure):
 problemas com dependências - a deixar por configurar
Nenhum relatório do apport gravado porque a mensagem de erro indica é o seguimento de um erro de uma falha anterior.
Foram encontrados erros enquanto processava:
 mumble-server
 mumble-server-web
E: Sub-process /usr/bin/dpkg returned an error code (1)


And this is the output of sudo apt-get upgrade
> 

A ler as listas de pacotes...
A construir árvore de dependências...
A ler a informação de estado...
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
2 pacotes não totalmente instalados ou removidos.
Após esta operação, serão utilizados 0B adicionais de espaço em disco.
Deseja continuar [Y/n]? A instalar mumble-server (1.1.7-3) ...
chmod: não consigo aceder a `/var/lib/mumble-server': Ficheiro ou directoria inexistente
dpkg: erro ao processar mumble-server (--configure):
 subprocesso post-installation script retornou erro do status de saída 1
dpkg: problemas com dependências impedem a configuração de mumble-server-web:
 mumble-server-web depende de mumble-server (>= 1.1.7-3); no entanto:
 O pacote mumble-server ainda não está configurado.
dpkg: erro ao processar mumble-server-web (--configure):
 problemas com dependências - a deixar por configurar
Nenhum relatório do apport gravado porque a mensagem de erro indica é o seguimento de um erro de uma falha anterior.
Foram encontrados erros enquanto processava:
 mumble-server
 mumble-server-web
E: Sub-process /usr/bin/dpkg returned an error code (1)


He complains a lot about mumble, if I try sudo apt-get remove mumble:
> 

A ler as listas de pacotes...
A construir árvore de dependências...
A ler a informação de estado...
O pacote mumble não está instalado, por isso não será removido
Os seguintes pacotes foram instalados automaticamente e já não são necessários:
  espeak libg15render1 kwin libportaudio2 libxevie1 espeak-data libspeechd2
  libg15daemon-client1 libespeak1 libg15-1 speech-dispatcher libdotconf1.0
Utilize 'apt-get autoremove' para os remover.
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
2 pacotes não totalmente instalados ou removidos.
Após esta operação, serão utilizados 0B adicionais de espaço em disco.
A instalar mumble-server (1.1.7-3) ...
chmod: não consigo aceder a `/var/lib/mumble-server': Ficheiro ou directoria inexistente
dpkg: erro ao processar mumble-server (--configure):
 subprocesso post-installation script retornou erro do status de saída 1
dpkg: problemas com dependências impedem a configuração de mumble-server-web:
 mumble-server-web depende de mumble-server (>= 1.1.7-3); no entanto:
 O pacote mumble-server ainda não está configurado.
dpkg: erro ao processar mumble-server-web (--configure):
 problemas com dependências - a deixar por configurar
Nenhum relatório do apport gravado porque a mensagem de erro indica é o seguimento de um erro de uma falha anterior.
Foram encontrados erros enquanto processava:
 mumble-server
 mumble-server-web
E: Sub-process /usr/bin/dpkg returned an error code (1)

He's not happy at all.

---

### Post by Monsieur Gonzalez on 2009-04-30
I had never heard about mumble (it's voip software), but seems unrelated with your problem. Try to post the log file for Xorg server (/var/log/Xorg.0.log), that might give a clue.

---

### Post by stakh on 2009-04-30
> **Monsieur Gonzalez said:**
> I had never heard about mumble (it's voip software), but seems unrelated with your problem. Try to post the log file for Xorg server (/var/log/Xorg.0.log), that might give a clue.

It's a very nice conference/gaming voip software.

Here is the /var/log/Xorg.0.log
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux me-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 30 20:22:13 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc Radeon Mobility X700 (PCIE) rev 0, Mem @ 0xc0000000/268435456, 0xb0100000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched radeon from file name radeon.ids
(==) Matched radeon for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 6.12.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI FirePro V8750 (FireGL),
	ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
	ATI Mobility RADEON HD 4850 X2, ATI Radeon 4800 Series,
	ATI FirePro RV770, AMD FireStream 9270, AMD FireStream 9250,
	ATI FirePro V8700 (FireGL), ATI Mobility RADEON HD 4870,
	ATI Mobility RADEON M98, ATI FirePro M7750, ATI M98, ATI M98,
	ATI M98, ATI Radeon RV730 (AGP), ATI FirePro M5750,
	ATI Radeon RV730 (AGP), ATI RV730XT [Radeon HD 4670],
	ATI RADEON E4600, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
	ATI Radeon HD Graphics, ATI Radeon Graphics,
	ATI Mobility Radeon HD Graphics, ATI Mobility Radeon Graphics,
	ATI Radeon Graphics
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): TOTO SAYS 00000000b0100000
(II) RADEON(0): MMIO registers at 0x00000000b0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Mobility Radeon X700 (M26) (PCIE)" (ChipID = 0x5653)
(--) RADEON(0): Linear framebuffer at 0x00000000c0000000
(II) RADEON(0): PCIE card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1558 SubsystemID: 0x0560
	IOBaseAddress: 0x2000
	Filename:             
	BIOS Bootup Message: 
Clevo-M560-M26 256MB ATOMBIOS BR14393B/rel9.10.1.0/CL204195                 

(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x7ffb000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x7ffb000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 350000
(II) RADEON(0): Default Memory Clock: 330000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 500000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 200000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.29.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 50000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 350.000000, mclk: 330.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=50000; xclk=40000
(WW) RADEON(0): LVDS Info:
XRes: 1680, YRes: 1050, DotClock: 119250
HBlank: 160, HOverPlus: 48, HSyncWidth: 32
VBlank: 46, VOverPlus: 2, VSyncWidth: 6
(II) RADEON(0): Skipping TV-Out
(II) RADEON(0): TMDS PLL from BIOS: 16500 b0112
encoder: 0x4
encoder: 0x1
encoder: 0x2
(II) RADEON(0): Output LVDS using monitor section Configured Monitor
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVDS
  DDC reg: 0x60
(II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT1: INTERNAL_DAC1
  DFP1: INTERNAL_TMDS1
  DDC reg: 0x60
Atom Get EDID success
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
finished output detect: 0
Atom Get EDID success
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
Unhandled monitor type 0
finished output detect: 1
finished all detect
before xf86InitialConfiguration
Atom Get EDID success
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEON(0): Added native panel mode: 1680x1050
Atom Get EDID success
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
Unhandled monitor type 0
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output LVDS using initial mode 1680x1050
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using EXA acceleration architecture
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): MM_TABLE: 00-66-c1-ea-0d-0a-ca-66-8b-d0-f7-c6-00-01
(II) RADEON(0): This card has MM_TABLE we do not recognize.
		If your card is TV-in capable you will need to specify options RageTheatreCrystal, RageTheatreTunerPort, 
		RageTheatreSVideoPort and TunerType in /etc/X11/xorg.conf.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit c0000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable LVDS
(II) RADEON(0): Dynamic Clock Scaling Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 262112 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x007e9000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x007ed000
(II) RADEON(0): Will use 8100 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 32 kb for PCI GART at offset 0x0fff8000
(II) RADEON(0): Will use 8100 kb for back buffer at offset 0x007f1000
(II) RADEON(0): Will use 8100 kb for depth buffer at offset 0x00fda000
(II) RADEON(0): Will use 118784 kb for textures at offset 0x017c3000
(II) RADEON(0): Will use 118996 kb for X Server offscreen at offset 0x08bc3000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xc0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [pci] 32768 kB allocated with handle 0xf9aef000
(II) RADEON(0): [pci] ring handle = 0xf9aef000
(II) RADEON(0): [pci] Ring mapped at 0xb77ea000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf9bf0000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb77e9000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf9bf1000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xa754b000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf9df1000
(II) RADEON(0): [pci] GART Texture map mapped at 0xa58cb000
(II) RADEON(0): [drm] register handle = 0xb0100000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000 0xcfffc000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xcfffc000 is: 0xcfffc000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xffffffc0
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000 0xcfffc000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) RADEON(0): num quad-pipes is 2
(II) EXA(0): Offscreen pixmap area of 121851904 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable LVDS
disable LVDS
init memmap
init common
init crtc1
init pll1
freq: 119250000
best_freq: 119250000
best_feedback_div: 106
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000 0xcfffc000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 444 x 277
(II) Synaptics touchpad driver version 0.99.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(II) Synaptics Touchpad: x-axis range 32 - 544
(II) Synaptics Touchpad: y-axis range 32 - 352
(II) Synaptics Touchpad: device does not report pressure, will use touch data.
(II) Synaptics Touchpad: finger width range 0 - 0
(II) Synaptics Touchpad: buttons: left right middle double triple
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: TOUCHPAD)
(**) Synaptics Touchpad: (accel) keeping acceleration scheme 1
(**) Synaptics Touchpad: (accel) filter chain progression: 2.00
(**) Synaptics Touchpad: (accel) filter stage 0: 20.00 ms
(**) Synaptics Touchpad: (accel) set acceleration profile 0
(--) Synaptics Touchpad touchpad found
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "pt"
(**) AT Translated Set 2 keyboard: xkb_layout: "pt"
(II) config/hal: Adding input device ETPS/2 Elantech Touchpad
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event7"
(II) ETPS/2 Elantech Touchpad: x-axis range 32 - 544
(II) ETPS/2 Elantech Touchpad: y-axis range 32 - 352
(II) ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
(II) ETPS/2 Elantech Touchpad: finger width range 0 - 0
(II) ETPS/2 Elantech Touchpad: buttons: left right middle double triple
(--) ETPS/2 Elantech Touchpad touchpad found
(**) ETPS/2 Elantech Touchpad: always reports core events
(II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
(**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
(**) ETPS/2 Elantech Touchpad: (accel) filter chain progression: 2.00
(**) ETPS/2 Elantech Touchpad: (accel) filter stage 0: 20.00 ms
(**) ETPS/2 Elantech Touchpad: (accel) set acceleration profile 0
(WW) ETPS/2 Elantech Touchpad can't grab event device, errno=16
(--) ETPS/2 Elantech Touchpad touchpad found
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "pt"
(**) Video Bus: xkb_layout: "pt"
Atom Get EDID success
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEON(0): Added native panel mode: 1680x1050
Atom Get EDID success
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Dac detection success
Unhandled monitor type 0
(II) AIGLX: Suspending AIGLX clients for VT switch
disable LVDS
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000 0xcfffc000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV

```
Hope this helps

---

### Post by Monsieur Gonzalez on 2009-05-01
Some ideas: 

1- Your server layout seems to be missing the keyboard, but I'm on a desktop here, maybe that's normal for a notebook. My Xorg.log for ServerLayout looks like this:

(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"

2- Have you tried the failsafe option in KDM? If your keyboard/touchpad work there, then it's a KDE problem, and you could try renaming your .kde folder to .kdeold and then copying your data to the newly created directory. 

3- If your keyboard/touchpad do not work in KDM's failsafe mode, then post your xorg.conf file here to check.

---

### Post by stakh on 2009-05-01
A stupid question: how do you start the KDM failsafe mode?

In the meantime, here is my /etc/X11/xorg.conf
> 

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection


---

### Post by stakh on 2009-05-01
> **stakh said:**
> A stupid question: how do you start the KDM failsafe mode?

What I mean is that in the Grub menu I can select recovery mode, but if I boot up, I'm directly thrown into a login menu that does not give me any choise as to the windows manager to load.

---

### Post by Monsieur Gonzalez on 2009-05-01
Sorry, I wasn't clear enought. In the KDM menu you can select the session you're starting (KDE, Gnome if you've installed it, and failsafe, or something like that, it might be different words, my menu is in spanish). That'll bring you to a console program and a very basic window manager. 

As for the xorg.conf, you can try to add the keyboard to the xorg.conf section. Make a backup first, just in case. 

Your "ServerLayout" section looks like this:

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Synaptics Touchpad"
EndSection 

I think it should look like this
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice    "Generic Keyboard" "CoreKeyboard"
InputDevice "Synaptics Touchpad"
EndSection

---

### Post by stakh on 2009-05-01
> **Monsieur Gonzalez said:**
> In the KDM menu you can select the session you're starting (KDE, Gnome if you've installed it, and failsafe, or something like that, it might be different words, my menu is in spanish). That'll bring you to a console program and a very basic window manager. 

The problem is that I am not presented with a KDM menu where I can select the session in which to start the graphical interface. The dialog I get befor launching kde is a login interface, where I can choose under which account I will login.

> As for the xorg.conf, you can try to add the keyboard to the xorg.conf section. Make a backup first, just in case. 

I tried your modification, but it did not change much. When I press Alt-F2, I ghet the application launcher, but I still can't type anything into it. The mouse cursor remains fixed at the center of the monitor.

---

### Post by Monsieur Gonzalez on 2009-05-01
In KDE, you're presented with a greeter, KDM, and you should have the user/password thing, and then on the right bottom of the screen two options, session and menu, and then time and date. Otherwise, run 'sudo dpkg-reconfigure kdm' to make it your default greeter.

As for the keyboard, you could try 'sudo dpkg-reconfigure xserver-xorg-input-kbd'. Other than that, if you have a 9.04 cd around, you could try booting with it and taking a look at the xorg.conf and see if there're differences.

Forgot to add that for changes to take place, you have to reboot the xserver (or the machine)

---

### Post by stakh on 2009-05-01
> **Monsieur Gonzalez said:**
> In KDE, you're presented with a greeter, KDM, and you should have the user/password thing, and then on the right bottom of the screen two options, session and menu, and then time and date. Otherwise, run 'sudo dpkg-reconfigure kdm' to make it your default greeter.

Ok, I got what you mean, and what I meant by the login interface is what you described. When I select the recovery option, or do the dpkg-reconfigure kdm thingy and go into the kdm mode, I'm instantly throw back to the same login interface. I have no other choice but to go via kde

> 
As for the keyboard, you could try 'sudo dpkg-reconfigure xserver-xorg-input-kbd
Tried it, but no changes.

> Other than that, if you have a 9.04 cd around, you could try booting with it and taking a look at the xorg.conf and see if there're differences.
When I launch from the CD, the main differences are that sound works (nice), and that the keyboard input works (very nice). However, the touchpad is still not working.

Here is the xorg.conf
```


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
It looks omniously empty...

> Forgot to add that for changes to take place, you have to reboot the xserver (or the machine)

I always reboot the machine, just to make sure

---

### Post by stakh on 2009-05-01
Ok, here's a follow-up:
Since launching the 9.04 CD allowed me to at least have the keyboard, I went on to try to solve the touchpad issue. I found the [following reference](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33):

> 
i solved my non working touchpad by doing in terminal:
modprobe -r psmouse
 modprobe psmouse proto=imps
at this time the touchpad should be working
and add: options psmouse proto=imps
 to: gedit /etc/modprobe.d/options


Now my keyboard and touchpad are fully functional when I launch jaunty from the CD... But I would really like to have it working from my "upgraded"/"messed up" installation.

---

### Post by stakh on 2009-05-01
Ok, I completed a fresh install of Jaunty!

Monsieur Gonzalez, thanks for the time and support, I appreciate a lot!

---

### Post by Monsieur Gonzalez on 2009-05-01
All's well that ends well. You're welcome.

---

