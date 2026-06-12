---
title: "es un bug o mal configurado hibernar ubuntu 7.10"
date: 2009-03-27
forum: Hardware
---

### Post by FMGS on 2009-03-27
Bueno espero no estar metiendo la pata pero me gustaria saber si el problema    de hibernar ubuntu 7.10 es un bug y hay que reportarlo o solo hay que configurar bien hibernar.
el caso es que  cuando suspendo mi laptop (HP F756LA ( amd64 x2 - 1 giga de ram - geforce 7000m/nforce 610 )).todo funciona de maravilla pero al hibernar cuando regresa de hibernar la pantalla queda negra  (parece que funciona todo solo no veo nada ,no se activa el video ).
Este es el problema ,la unica forma en la que pude parcialmente solucionarlo fue que cuando queda la pantalla negra pongo suspender y cuando retorno de la  suspencion funciona todo como corresponde .
yo creo en mi ingnorancia en la materia  que quisa sea algo sencillo de solucionar por algun experto de sistemas linux.
Por lo demas ubuntu 7.10  32bits funciona de maravilla en este laptop


nota : he probado 8.10 esta muy bueno pero ya al inicio del systema debo presionar cualquier tecla durante la primera fase de arranque por que se queda como espeeando y no sigue la carga y alactualizar tambien tube errores quizas al ser un notebook  no ifrntifica bien mi hardware.
pero igual estoy muy contento con ubuntu el 7.10 es exelente para la compaq presario F756LA (aunque los de HP apestan (pero esa es otra historia)) 

sin mas que agradecer al software libre espero que esto inspire a algun genio de ubuntu para solucionar este pequeño problema.:P

---

### Post by FMGS on 2009-03-29
Bueno ya que no encontre respuesta no pude resistir en investigar de forma burda el problema .
Ignorante en cuanto a scripts . pero con un conocimientos basico/medio en programacion de sistemas Msdos (turbo pascal /turbo c / turbo basic y asm) me lance a tratar de resolver este  pequeno problema.
Hasta donde entiendo yo las funciones suspender e hibernar funciona salvo que  al retorno de la hibernacion la pantalla queda oscura.
aqui esta el problema la pantalla queda oscura.
Bueno si ponemos nuevamente suspender (estando la pantalla a oscura ) en mi caso  tecla Funcion + tecla F5 presionada unos segundos  comienza la suspencion normalmente, unos segundos despues entra en suspencion . En mi caso toco cualquier tecla y listos se despierta  me pide el la clave de ingreso y  me muestra el escritorio como lo habia desjado durante la hibernacion.
dedusco que modificando algunos scripts podria solucionarlo.
mi primer intencion es crear un script que suspenda y despierte la maquina automaticamente,
lo ideal seria encontrar el que activa la pantalla.
si algun  usuario de ubunto  u otra version de linux tiene informacion sobre el tema estaria muy agradecido.
:P

---

### Post by FMGS on 2009-03-29
es un bug o mal configurado hibernar ubuntu 7.10  Reply to Thread (SOLUCIONADO  100% para HP Compaq Presario F756la )
Bueno finalmente solucione el problema que tenia con HIBERNAR 
la solucion la trajo ENVY (lo instale y actalizo mi controlador nvidia .ademas habilita otras funciones de video).
Instale ENVY reinicie la pc y efectue las pruebas de suspeder  y funciono perfectamente igual que el controlador anterior.
la prueba de HIBERNAR : puse hibernar y comienza todo bien pero no apagaba la pc.
revice desde la consola los comandos sudo hal (para apagar) y se apago
inicie la maquina y se recupero perfectamente de la hibernacion.
finalmente me faltaba  que se apague  entonces mire el archivo de configuracion ACPI mediante 

------------------------------------o-----------------------------------
sudo gedit /etc/default/acpi-support
------------------------------------o-----------------------------------

y quedo asi 
------------------------------------o-----------------------------------

# archivo   /etc/default/acpi-support
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
# ENABLE_LAPTOP_MODE=true
ENABLE_LAPTOP_MODE=true

# Spindown time on battery
SPINDOWN_TIME=12

-----------------------------------o------------------------------------


grabe la modificacion que no me acuerdo cual era(por que hice algunas modificasiones y no las comente ) por eso pongo la copia del archivo.
guarde el archivo y fui al escritorio abri un par de juegos  el explorador   
 y por ultimo  use en hibernacion .
ubuntu se cerro perfectamente .
reinicie y se recupero de la hibernacion perfectamente,el escritorio estaba como lo deje y todo funciona de maravilla.
 AGUANTE  UBUNTU  y viva el software  libre
ya puedo festejar :P:guitar:
:guitar:

---

