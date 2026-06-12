---
title: "Otra vez mi GeForce 5500, ahora en Jaunty"
date: 2009-05-07
forum: Hardware
---

### Post by guidito73 on 2009-05-07
Bueno, me mudé felizmente a Jaunty... No tan felizmente...

Tuve el mismo problema que con Hardy, en cuanto a la configuración de la resolución de la pantalla. Instalé los drivers privativos, Envyng de por medio, modifiqué el Xorg.conf (de hecho, levanté una copia que tenía hecha en el /home de cuando quedó funcionando bien en Hardy) pero el problema es que parece que Jaunty no está reconociendo bien el monitor (los 1024X768 hacen que tenga que hacer un scroll porque la resolución real es 640X480 y se ve todo pixelado).

Y bien, me sacaron el displayconfig-gtk... Hasta ahora no pude encontrar nada para arreglaro =s

Alguna ayuda?

Dejo el contenido de mi xorg.conf:

```
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
	modeline  "1024x768@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0 "Default Screen" 0 0
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce FX (generic)"
	Busid		"PCI:1:0:0"
	Screen	0
	Vendorname	"NVIDIA"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"NVIDIA GeForce FX (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection

```

---

### Post by guillermolisi on 2009-05-07
> **guidito73 said:**
> Bueno, me mudé felizmente a Jaunty... No tan felizmente...

Tuve el mismo problema que con Hardy, en cuanto a la configuración de la resolución de la pantalla. Instalé los drivers privativos, Envyng de por medio, modifiqué el Xorg.conf (de hecho, levanté una copia que tenía hecha en el /home de cuando quedó funcionando bien en Hardy) pero el problema es que parece que Jaunty no está reconociendo bien el monitor (los 1024X768 hacen que tenga que hacer un scroll porque la resolución real es 640X480 y se ve todo pixelado).

Y bien, me sacaron el displayconfig-gtk... Hasta ahora no pude encontrar nada para arreglaro =s

Alguna ayuda?

Dejo el contenido de mi xorg.conf:

```
Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Plug 'n' Play"
    Modelname    "Plug 'n' Play"
    modeline  "1024x768@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
    Gamma    1.0
EndSection

Section "Monitor"
    Identifier    "monitor1"
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth    24
        Virtual    1024    768
        Modes        "1024x768@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
EndSection

Section "Module"
    Load        "glx"
    Load        "v4l"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "es"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    screen 0 "Default Screen" 0 0
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "NVIDIA GeForce FX (generic)"
    Busid        "PCI:1:0:0"
    Screen    0
    Vendorname    "NVIDIA"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "Device"
    Identifier    "device1"
    Boardname    "NVIDIA GeForce FX (generic)"
    Busid        "PCI:1:0:0"
    Driver        "nv"
    Screen    1
    Vendorname    "NVIDIA"
EndSection

```
Ya que tenes copia del xorg.conf, probaste con reconfigurar el X server a ver que resulta ? Total ahora no funciona, no tenes nada que perder, peor no puede estar.

Para reconfigurarlo ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` (esta al principio del archivo xorg.conf, por si no queres consultar de nuevo el post).

---

