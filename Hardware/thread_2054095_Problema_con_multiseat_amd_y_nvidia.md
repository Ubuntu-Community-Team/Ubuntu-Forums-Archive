---
title: "Problema con multiseat amd y nvidia"
date: 2012-09-06
forum: Hardware
---

### Post by kamiloxnumetal on 2012-09-06
Hola saludos a todos soy nuevo aca aunque uso ubuntu y sus derivados hace tiempo ahora estoy con kubuntu

Tengo dos problemas bastante rebuscados y ojala me pueda ayudar

Tengo un multiseat con 2 estaciones o seats
con 2 tarjetas de video

El primer problema es que una tarjeta de video es amd (AMD Radeon HD 6450) y la otra es nvidia (Nvidia GeForce 6100)

Como sabran los gestores de paquetes no dejan instalar y tener activos los drivers de amd (fglrx) y nvidia (nvidia, nvidia-current) al mismo tiempo

Bueno me las arregle y instale fglrx por el gestor y el driver de nvidia lo instale manualmente con el .run de la pagina de nvidia, de esa forma puedo hacer que ambos drivers se ejecuten a la vez en instancias separadas de X

Pero la gpu nvidia no puede usar openGL  D:  ... , me dice

```

seat2@kamiloxnumetal-desktop:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
seat2@kamiloxnumetal-desktop:~$ 

```

Tambien si trato de usar nvidia-settings no puedo, me sale

```

seat2@kamiloxnumetal-desktop:~$ nvidia-settings
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 158 error_code 1 request_code 136 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
seat2@kamiloxnumetal-desktop:~$ 

```

A pesar de ello si configuro manualmente cosas en .nvidia-settings-rc , y cargo nvidia-settings la configuracion de brillo, contraste y todo eso se carga y el monitor cambia, pero sale el mismo error

no puedo usar nvidia-xconfig y tampoco puedo dejar que el instalador del driver de nvidia me configure nvidia-settings 
porque arruinan mi xorg.conf (borran toda la parte de amd) y por ende la config multiseat

Dejo mi kdmrc y xorg.conf

/etc/kde4/kdmrc
```

[General]
ConfigVersion=2.4
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
GreeterUID=kdm
PidFile=/var/run/kdm.pid
ReserveServers=:2,:3
ServerVTs=7,9
StaticServers=:0,:1

[Shutdown]
BootManager=None
HaltCmd=/sbin/shutdown -h -P now
RebootCmd=/sbin/shutdown -r now

[X-*-Core]
AllowNullPasswd=false
AllowRootLogin=false
AllowShutdown=Root
AutoReLogin=false
ClientLogFile=.xsession-errors-%d
Reset=/etc/kde4/kdm/Xreset
Session=/etc/kde4/kdm/Xsession
SessionsDirs=/usr/share/xsessions,/var/lib/menu-xdg/xsessions,/etc/kde4/kdm/sessions,/usr/share/kde4/apps/kdm/sessions
Setup=/etc/kde4/kdm/Xsetup
Startup=/etc/kde4/kdm/Xstartup

[X-*-Greeter]
AntiAliasing=false
ColorScheme=
FaceSource=AdminOnly
FailFont=Sans Serif,10,-1,5,75,0,0,0,0,0
GUIStyle=
GreetFont=Serif,20,-1,5,50,0,0,0,0,0
GreetString=Bienvenido a %s en %n
GreeterPos=50,50
HiddenUsers=
Language=en_GB
LogoArea=Logo
LogoPixmap=/usr/share/kde4/apps/kdm/pics/kdelogo.png
MaxShowUID=29999
MinShowUID=1000
Preloader=/usr/bin/preloadkde
SelectedUsers=
ShowUsers=NotHidden
SortUsers=true
StdFont=Sans Serif,10,-1,5,50,0,0,0,0,0
Theme=/usr/share/kde4/apps/kdm/themes/black_diamond
UseBackground=true
UseTheme=true
UserCompletion=false
UserList=true

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-br -nolisten tcp
ServerCmd=/usr/bin/X

[X-:*-Greeter]
AllowClose=true
DefaultUser=kamiloxnumetal
FocusPasswd=true
LoginMode=DefaultLocal
PreselectUser=Previous

[X-:0-Core]
AutoLoginEnable=true
AutoLoginLocked=false
AutoLoginUser=kamiloxnumetal
ClientLogFile=.xsession-errors
ServerCmd=/usr/bin/X -sharevts -layout layout0 -isolateDevice PCI:1:0:0 -keeptty
ServerVT=7

[X-:0-Greeter]
DefaultUser=

[X-:1-Core]
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=
ClientLogFile=.xsession-errors
ServerCmd=/usr/bin/X -sharevts -novtswitch -layout layout1 -isolateDevice PCI:0:2:0 -keeptty
ServerVT=9

[X-:1-Greeter]
DefaultUser=

[Xdmcp]
Enable=false
Willing=/etc/kde4/kdm/Xwilling


```

/etc/X11/xorg.conf
```

##################### NVIDIA GEFORCE 6100 SEAT ####################

Section "ServerLayout"
	Identifier     "Layout1"
	Screen      0  "Screen1" 0 0
	InputDevice    "Keyboard1" "CoreKeyboard"
	InputDevice    "Mouse1" "CorePointer"
	Option	    "AutoEnableDevices" "false"
	Option	    "AutoAddDevices" "false"
	Option	    "AllowEmptyInput" "true"
EndSection

Section "InputDevice"
	#Option	    "Protocol" "auto"
	#Option	    "Emulate3Buttons" "no"
	#Option	    "ZAxisMapping" "4 5"
	Identifier  "Mouse1"
	Driver      "evdev"
	Option	    "Device" "/dev/input/by-path/platform-i8042-serio-1-event-mouse"
	#Option	    "Device" "/dev/input/mouse1"
	Option	    "GrabDevice" "on"
EndSection

Section "InputDevice"
	Identifier  "Keyboard1"
	Driver      "evdev"
	Option	    "Device" "/dev/input/by-path/platform-i8042-serio-0-event-kbd"
	Option	    "XkbRules" "xorg"
	#Option	    "XkbModel" "105"
	Option	    "XkbLayout" "es"
	Option	    "Protocol" "Standard"
EndSection

Section "Monitor"
	Identifier   "Compaq MV520 CRT"
	VendorName   "Unknown"
	ModelName    "COMPAQ MV520"
	HorizSync    30.0 - 54.0
	VertRefresh  50.0 - 100.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Device1"
	Driver      "nvidia"
	VendorName  "NVIDIA Corporation"
	BoardName   "GeForce 6100"
	Option         "RenderAccel" "true"
	#Option         "TripleBuffer" "true"
	Option         "NoLogo" "1"
	BusID       "PCI:0:5:0"
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Device1"
	Monitor    "Compaq MV520 CRT"
	DefaultDepth     24
	Option	    "TwinView" "0"
	Option	    "metamodes" "1024x768 +0+0; nvidia-auto-select +0+0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

##################### NVIDIA GEFORCE 6100 SEAT ####################
##################### AMD RADEON HD 6450 SEAT #####################

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
	Option	    "AutoEnableDevices" "false"
	Option	    "AutoAddDevices" "false"
	Option	    "AllowEmptyInput" "true"
EndSection

Section "InputDevice"
	#Option	    "Protocol" "auto"
	#Option	    "Emulate3Buttons" "no"
	#Option	    "ZAxisMapping" "4 5"
	Identifier  "Mouse0"
	Driver      "evdev"
	Option	    "Device" "/dev/input/by-path/pci-0000:00:0b.0-usb-0:2:1.0-event-mouse"
	Option	    "GrabDevice" "on"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "evdev"
	Option	    "Device" "/dev/input/by-path/pci-0000:00:0b.0-usb-0:4:1.0-event-kbd"
	Option	    "XkbRules" "xorg"
	#Option	    "XkbModel" "105"
	Option	    "XkbLayout" "es"
	Option	    "Protocol" "Standard"
EndSection

Section "Monitor"
	Identifier  "AOC FT720g CRT"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Device0"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "AOC FT720g CRT"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Device0"
	DefaultDepth     24
	Option         "Monitor-CRT1" "AOC FT720g CRT"
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

##################### AMD RADEON HD 6450 SEAT #####################
######################### OTHER CONFIG ############################

Section "Module"
	Load  "dbe"
	Load  "extmod"
	Load  "type1"
	Load  "freetype"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option         "AutoAddDevices" "false"
	Option         "AutoEnableDevices" "false"
	Option         "AllowMouseOpenFail" "on"
	Option         "AllowEmptyInput" "on"
	Option         "ZapWarning" "on"
	Option         "DontZap" "false"
	Option         "HandleSepcialKeys" "off"
	Option         "DRI2" "on"
	Option         "Xinerama" "off"
EndSection

######################### OTHER CONFIG ############################



```

Lo que quiero es hacer que nvidia-settings funcione, y que funcione openGL en la seat con nvidia, eso sin arruinar fglrx ni catalyst control center

Bueno mi segundo problema:

El usuario en el segundo seat no puede montar unidades usb como pendrives discos duros extraibles etc, si los monta el usuario del otro seat quedan con permisos para el y el seat tampoco puede leerlos

bueno ojala me ayuden he preguntado en muchas partes y nadie sabe del tema

---

### Post by dnovai on 2013-04-22
Revisa este thread ([http://ubuntuforums.org/showthread.php?t=2064162](http://ubuntuforums.org/showthread.php?t=2064162)). Lo mas probable es que tengas mal instalado los drivers o controladores de tu tarjeta nvidia.
Saludos!

---

