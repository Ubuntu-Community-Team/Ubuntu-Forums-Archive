---
title: "Se me cae el sistema cuando escucho musica en Ubuntu 9.04"
date: 2009-06-24
forum: Hardware
---

### Post by F.Y.N. on 2009-06-24
Holanda.

Hace un par de días que estoy "jugando" con Ubuntu y uno de los pocos problemas que me queda por resolver, es que cuando escucho música en "Rhythmbox" o "Audacious", no pasan más de  dos o tres canciones y el sonido se corta (suena como "crik trk trk"), y de ahí vienen mas problemas: el sistema se pone muy, muy lento (incluso el puntero del mouse se queda pegado por algunos segundos), los programas de audio se bloquean, ninguna otra cosa vuelve a sonar y no me queda otra alternativa más que reiniciar, y cuando vuelvo del reinicio todas las configuraciones del "control de volumen" se pierden y queda todo en máximo volumen y el micrófono queda con el típico "piiiiii" (casi quedo sordo la primera vez que me paso este problema ¬¬).

Y otras veces pasa que el sistema derechamente se bloquea y no responde a nada y tengo que reiniciar el PC con el boton de reset.

Busque y busque, y encontre que esto era un bug de Pulseaudio, así que lo desinstale y ahora creo que estoy usando "ALSA", pero la cosa sigue igual, al rato de escuchar música el sistema se me cae, a veces a los 10 segundos, a veces a la media hora y ya me tiene chato esto...

Mi tarjeta de sonido, según lspci es:

00:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

Tengo un Pentium 4 HT de 3.0 GHz, 768 MB de RAM, t. de video Geforce 6200 y placa Asrock P4775VM800.

Salu1+1

---

### Post by Psycopatologic on 2009-06-24
Eso amigo mio es problema del driver de audio usado por ubuntu que se llama Pulseaudio. Si tu abres terminal y ejecutas el comando top, el uso de CPU lo encabeza este proceso y es por esa razon que ubuntu se cuelga. A mi me pasa lo mismo. Googleando la respuesta encontre la posibilidad de cambiar los drivers de audio por defecto (Pulseaudio) por ALSA que son drivers desarrollados para el mismo fin pero que no son usados por defecto en ubuntu. Lo que recomiendo es:

1º Usa como reproductor de audio Banshee, es identico a rythmbox pero mas liviano, versatil y rapido.

2º No cambies de canciones muy rapido por que eso tambien ayuda a colapsar Pulseaudio.

3º En el panel superior agrega un monitor de sistema (boton derecho sobre el panel>agregar al panel>monitor de sistema) asi puedes estimar los momentos de mayor consumo de CPU por parte de tu reproductor y el driver pulseaudio.

4º No escuches musica con el firefox abierto en una pagina hecha con flash ya que flash es uno de los principales causales de cuelgues de pulseaudio.

5º Si se te cuelga, intenta con los comandos

$ sudo pulseaudio -k

$ sudo pulseaudio -d

matas y cargas el proceso.

6º Si nada de esto funciona intenta cambiar a ALSA pero OJO bajo tu propio riesgo. Mucha gente dice que le funciona perfecto, pero no todos los pc son iguales. 

Ventajas:

- Pc mas estable, sin cuelgues por pulseaudio y quizas una mayor calidad de sonido.

Desventajas:

-Pierdes sonido de sistema como al iniciar sesion, los bongo del login o sonidos que hayas puesto tu.
-Al ser un driver no por defecto de Ubuntu quizas te genere errores de compatibilidad.
-Puede que te quedes sin sonido derechamente teniendo que reinstalar Pulseaudio como ultima esperanza.

Espero te sirva de algo, si despues de haber instalado ALSA como nos dijiste sigues con el problema, no desinstalaste bien Pulseaudio o no instalaste correctamente ALSA.

Saludos

---

### Post by F.Y.N. on 2009-06-24
Lo desinstale con esta guía: [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

Así que pulseaudio ya no existe (incluso probé y dice algo como "bash: error o comando no encontrado").

Ahora si me pudieras decir como comprobar que ALSA quedo funcionando como se debe te lo agradecería. Si suena al inicio y todo, si no es que se me haya ido el sonido, sino que cuando escucho música (con el player que sea da lo mismo; he probado como con 4), al rato se bloquea o se cae el audio igual, sea una sola canción o pasen 10, este navegando o no este haciendo nada mas que oír música, es aleatorio.

Anteriormente cuando el Pulseaudio se caía tampoco lo podía matar, ni con kill -9, ni desde el monitor de sistema, ni con nada, por eso decía que el único recurso que me quedaba (y me sigue quedando) es reiniciar, a veces desde el sistema otra veces directamente del boton porque se bloquea por completo.

Salu1+1

---

### Post by Psycopatologic on 2009-06-24
Y estas 100% seguro que es problema del audio? ubuntu puede sufrir cuelgues por mil razones y la interrupcion del sonido es un sintoma. La proxima vez que te pase intenta abrir un terminal, como sea, dale tiempo, apaga los parlantes si es muy feo el sonido y le mandas el comando top.

user@user:~$ top

y pegas lo que sale.

Para comprobar que esta instalado solo ves en el recuadro que dice "Devices" como dice el tuto y pones Test a cada uno, si todo anda Ok no tendria que haber problemas. Intentalo, quizas no es el problema del audio.

---

### Post by CdK1 on 2009-06-24
sudo apt-get install alsa-base alsa-oss
sudo alsaconf
alsamixer

Ahora, no debería caerse usando PulseAudio, te recomiendo que cuando pase eso, al loguearte pongas dmesg y ve las últimas líneas antes del reinicio, además pon ALSA en el gnome-volume ;)

---

### Post by moreback on 2009-06-25
> **Psycopatologic said:**
> Eso amigo mio es problema del driver de audio usado por ubuntu que se llama Pulseaudio.
Estimado, por favor infórmese bien antes de decir semejante estupidez: [PulseAudio]("http://www.pulseaudio.org/") es un servidor de sonido, [ALSA]("http://es.wikipedia.org/wiki/Arquitectura_de_Sonido_Avanzada_para_Linux") es realmente el que tiene los drivers de audio.

Saludos.

---

### Post by AlvaroV on 2009-06-25
Pero al margen de lo equivocado que se pueda estar con drivers y eso. Yo llevo como dos días escuchando CD porque escuchando con Rhyt o Totem archivos mp3 del disco duro, después de un par de canciones se pega todo el sistema. Esto si, ocurre preferentemente cuando navego por internet al mismo timpo. Estos hechos no ocurrían con Windows :)....es broma iba a decir con ubuntu 8.04.

---

### Post by moreback on 2009-06-25
Eso puede ser por el plugin de flash.

---

### Post by F.Y.N. on 2009-06-25
> **Psycopatologic said:**
> Y estas 100% seguro que es problema del audio? ubuntu puede sufrir cuelgues por mil razones y la interrupcion del sonido es un sintoma. La proxima vez que te pase intenta abrir un terminal, como sea, dale tiempo, apaga los parlantes si es muy feo el sonido y le mandas el comando top.
[B]
user@user:~$ top[/B]

y pegas lo que sale.

Para comprobar que esta instalado solo ves en el recuadro que dice "Devices" como dice el tuto y pones Test a cada uno, si todo anda Ok no tendria que haber problemas. Intentalo, quizas no es el problema del audio.

Bueno, se me volvió a caer y esto me sale:

> top - 16:10:09 up 37 min,  2 users,  load average: 1.41, 1.75, 1.47
Tasks: 132 total,   4 running, 128 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.1%us,  9.2%sy,  0.0%ni, 47.0%id,  0.6%wa, 29.0%hi,  0.1%si,  0.0%st
Mem:    767536k total,   736068k used,    31468k free,    96088k buffers
Swap:   321260k total,     4884k used,   316376k free,   323356k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 2834 root      20   0  102m  43m 8992 R   46  5.9   6:44.96 Xorg                                                                                            
 3416 fabian    20   0 49892  25m 3556 R   17  3.4   1:29.62 compiz.real                                                                                     
 3575 fabian    20   0  216m  93m  21m R   15 12.5   4:02.95 firefox                                                                                         
 3629 fabian    20   0 35312  10m 4728 S    4  1.4   0:01.72 gnome-terminal                                                                                  
 3493 fabian    20   0 17188 2532 1084 S    2  0.3   0:11.08 gnome-screensav                                                                                 
 3422 fabian    20   0 23300 6292 4372 S    1  0.8   0:09.94 multiload-apple                                                                                 
 3432 fabian    20   0 21340 8164 3724 S    1  1.1   0:08.45 emerald                                                                                         
 2493 messageb  20   0  3076 1204  656 S    0  0.2   0:00.52 dbus-daemon                                                                                     
 2775 root      20   0  5180  784  572 S    0  0.1   0:00.48 hald-addon-stor                                                                                 
 4953 fabian    20   0  2448 1196  912 R    0  0.2   0:00.23 top                                                                                             
    1 root      20   0  3084  368  316 S    0  0.0   0:01.25 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.24 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.16 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0                                                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.01 events/1                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0                                                                                         
   13 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1                                                                                         
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                   
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                   
   16 root      15  -5     0    0    0 S    0  0.0   0:00.06 kblockd/0                                                                                       
   17 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                       
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue                                                                                          
   21 root      15  -5     0    0    0 S    0  0.0   0:00.11 ata/0                                                                                           
   22 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                                                                           
   23 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
   24 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
   25 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
   26 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                         
   27 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmmcd                                                                                           
   28 root      15  -5     0    0    0 S    0  0.0   0:00.00 btaddconn                                                                                       
   29 root      15  -5     0    0    0 S    0  0.0   0:00.00 btdelconn                                                                                       
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
   31 root      20   0     0    0    0 S    0  0.0   0:00.12 pdflush                                                                                         
   32 root      15  -5     0    0    0 S    0  0.0   0:02.97 kswapd0                                                                                         
   33 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
   34 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
   35 root      15  -5     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                                                                 
   38 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                       
   39 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1

Estaba usando el Audacious y navegando con FF.

Salu1+1

---

### Post by Carlos C on 2009-06-26
Hola, luego de un cuelgue te recomiendo que hagas lo que dice Cdk1. que escribas en el terminal:
```
dmesg
```
y veas si existe algún error que indique lo que puede estar fallando.

---

### Post by kamus on 2009-06-26
> **F.Y.N. said:**
> Holanda.

Hace un par de días que estoy "jugando" con Ubuntu y uno de los pocos problemas que me queda por resolver, es que cuando escucho música en "Rhythmbox" o "Audacious", no pasan más de  dos o tres canciones y el sonido se corta (suena como "crik trk trk"), y de ahí vienen mas problemas: el sistema se pone muy, muy lento (incluso el puntero del mouse se queda pegado por algunos segundos), los programas de audio se bloquean, ninguna otra cosa vuelve a sonar y no me queda otra alternativa más que reiniciar, y cuando vuelvo del reinicio todas las configuraciones del "control de volumen" se pierden y queda todo en máximo volumen y el micrófono queda con el típico "piiiiii" (casi quedo sordo la primera vez que me paso este problema ¬¬).

Y otras veces pasa que el sistema derechamente se bloquea y no responde a nada y tengo que reiniciar el PC con el boton de reset.

Busque y busque, y encontre que esto era un bug de Pulseaudio, así que lo desinstale y ahora creo que estoy usando "ALSA", pero la cosa sigue igual, al rato de escuchar música el sistema se me cae, a veces a los 10 segundos, a veces a la media hora y ya me tiene chato esto...

Mi tarjeta de sonido, según lspci es:

00:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

Tengo un Pentium 4 HT de 3.0 GHz, 768 MB de RAM, t. de video Geforce 6200 y placa Asrock P4775VM800.

Salu1+1

Que version del controlador para la tarjeta NVIDIA estas usando?

Saludos

---

### Post by F.Y.N. on 2009-06-26
> **Carlos C said:**
> Hola, luego de un cuelgue te recomiendo que hagas lo que dice Cdk1. que escribas en el terminal:
```
dmesg
```y veas si existe algún error que indique lo que puede estar fallando.

No se como determinar un error en esto que me sale:
> [    0.004000]     vmalloc : 0xf07b0000 - 0xff3fe000   ( 236 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xeffb0000   ( 767 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc05039df - 0xc0728e60   (2197 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05039df   (4110 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.45 BogoMIPS (lpj=11998904)
[    0.004037] Security Framework initialized
[    0.004045] SELinux:  Disabled at boot.
[    0.004067] AppArmor: AppArmor initialized
[    0.004079] Mount-cache hash table entries: 512
[    0.004245] Initializing cgroup subsys ns
[    0.004251] Initializing cgroup subsys cpuacct
[    0.004254] Initializing cgroup subsys memory
[    0.004260] Initializing cgroup subsys freezer
[    0.004282] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004286] CPU: L2 cache: 2048K
[    0.004290] CPU: Physical Processor ID: 0
[    0.004292] CPU: Processor Core ID: 0
[    0.004296] using mwait in idle threads.
[    0.004309] Checking 'hlt' instruction... OK.
[    0.023596] ACPI: Core revision 20080926
[    0.026268] ACPI: Checking initramfs for custom DSDT
[    0.313224] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.352922] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[    0.356001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6000.20 BogoMIPS (lpj=12000408)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.444567] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[    0.444598] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.448001] Measured 6983000520 cycles TSC warp between CPUs, turning off TSC clock.
[    0.448001] Marking TSC unstable due to check_tsc_sync_source failed
[    0.448075] Brought up 2 CPUs
[    0.448081] Total of 2 processors activated (11999.65 BogoMIPS).
[    0.448321] CPU0 attaching sched-domain:
[    0.448325]  domain 0: span 0-1 level SIBLING
[    0.448329]   groups: 0 1
[    0.448337] CPU1 attaching sched-domain:
[    0.448340]  domain 0: span 0-1 level SIBLING
[    0.448343]   groups: 1 0
[    0.448453] net_namespace: 776 bytes
[    0.448453] Booting paravirtualized kernel on bare hardware
[    0.448494] Time: 14:47:01  Date: 06/26/09
[    0.448494] regulator: core version 0.5
[    0.448494] NET: Registered protocol family 16
[    0.448494] EISA bus registered
[    0.448494] ACPI: bus type pci registered
[    0.448494] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.448494] PCI: Using configuration type 1 for base access
[    0.452311] ACPI: EC: Look up EC in DSDT
[    0.460791] ACPI: Interpreter enabled
[    0.460797] ACPI: (supports S0 S1 S3 S4 S5)
[    0.460825] ACPI: Using IOAPIC for interrupt routing
[    0.468871] ACPI: No dock devices found.
[    0.468931] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.469005] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xefffffff]
[    0.469345] pci 0000:00:01.0: supports D1
[    0.469394] pci 0000:00:09.0: reg 10 io port: [0xc000-0xc0ff]
[    0.469440] pci 0000:00:09.0: supports D1 D2
[    0.469491] pci 0000:00:0f.0: reg 10 io port: [0xec00-0xec07]
[    0.469500] pci 0000:00:0f.0: reg 14 io port: [0xe800-0xe803]
[    0.469508] pci 0000:00:0f.0: reg 18 io port: [0xe400-0xe407]
[    0.469516] pci 0000:00:0f.0: reg 1c io port: [0xe000-0xe003]
[    0.469524] pci 0000:00:0f.0: reg 20 io port: [0xdc00-0xdc0f]
[    0.469532] pci 0000:00:0f.0: reg 24 io port: [0xd800-0xd8ff]
[    0.469609] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.469700] pci 0000:00:10.0: reg 20 io port: [0xc400-0xc41f]
[    0.469722] pci 0000:00:10.0: supports D1 D2
[    0.469724] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469730] pci 0000:00:10.0: PME# disabled
[    0.469789] pci 0000:00:10.1: reg 20 io port: [0xc800-0xc81f]
[    0.469811] pci 0000:00:10.1: supports D1 D2
[    0.469813] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469818] pci 0000:00:10.1: PME# disabled
[    0.469877] pci 0000:00:10.2: reg 20 io port: [0xcc00-0xcc1f]
[    0.469899] pci 0000:00:10.2: supports D1 D2
[    0.469901] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469906] pci 0000:00:10.2: PME# disabled
[    0.469965] pci 0000:00:10.3: reg 20 io port: [0xd000-0xd01f]
[    0.469987] pci 0000:00:10.3: supports D1 D2
[    0.469989] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469994] pci 0000:00:10.3: PME# disabled
[    0.470031] pci 0000:00:10.4: reg 10 32bit mmio: [0xfebff800-0xfebff8ff]
[    0.470075] pci 0000:00:10.4: supports D1 D2
[    0.470077] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.470082] pci 0000:00:10.4: PME# disabled
[    0.470160] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.470218] pci 0000:00:12.0: reg 10 io port: [0xd400-0xd4ff]
[    0.470226] pci 0000:00:12.0: reg 14 32bit mmio: [0xfebffc00-0xfebffcff]
[    0.470265] pci 0000:00:12.0: supports D1 D2
[    0.470267] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.470272] pci 0000:00:12.0: PME# disabled
[    0.470336] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.470344] pci 0000:01:00.0: reg 14 32bit mmio: [0xc0000000-0xcfffffff]
[    0.470351] pci 0000:01:00.0: reg 18 32bit mmio: [0xfc000000-0xfcffffff]
[    0.470371] pci 0000:01:00.0: reg 30 32bit mmio: [0xfeae0000-0xfeafffff]
[    0.470428] pci 0000:00:01.0: bridge 32bit mmio: [0xfaa00000-0xfeafffff]
[    0.470434] pci 0000:00:01.0: bridge 32bit mmio pref: [0xbff00000-0xdfefffff]
[    0.470444] bus 00 -> node 0
[    0.470452] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.470813] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.481951] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.482106] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.482256] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.482404] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.482553] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.482702] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.482851] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.483000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.483187] ACPI: WMI: Mapper loaded
[    0.483252] SCSI subsystem initialized
[    0.483252] libata version 3.00 loaded.
[    0.483252] usbcore: registered new interface driver usbfs
[    0.483252] usbcore: registered new interface driver hub
[    0.483252] usbcore: registered new device driver usb
[    0.483252] PCI: Using ACPI for IRQ routing
[    0.488016] Bluetooth: Core ver 2.13
[    0.488036] NET: Registered protocol family 31
[    0.488036] Bluetooth: HCI device and connection manager initialized
[    0.488036] Bluetooth: HCI socket layer initialized
[    0.488036] NET: Registered protocol family 8
[    0.488036] NET: Registered protocol family 20
[    0.488049] NetLabel: Initializing
[    0.488051] NetLabel:  domain hash size = 128
[    0.488053] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.488071] NetLabel:  unlabeled traffic allowed by default
[    0.488167] AppArmor: AppArmor Filesystem Enabled
[    0.492014] pnp: PnP ACPI init
[    0.492026] ACPI: bus type pnp registered
[    0.495607] pnp: PnP ACPI: found 9 devices
[    0.495610] ACPI: ACPI bus type pnp unregistered
[    0.495615] PnPBIOS: Disabled by ACPI PNP
[    0.495630] system 00:05: ioport range 0x295-0x296 has been reserved
[    0.495634] system 00:05: ioport range 0x3e0-0x3e7 has been reserved
[    0.495637] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.495640] system 00:05: ioport range 0x800-0x87f has been reserved
[    0.495643] system 00:05: ioport range 0x400-0x41f has been reserved
[    0.495646] system 00:05: iomem range 0xfff80000-0xffffffff has been reserved
[    0.495654] system 00:06: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.495657] system 00:06: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.495665] system 00:08: iomem range 0x0-0x9ffff could not be reserved
[    0.495669] system 00:08: iomem range 0xe0000-0xfffff could not be reserved
[    0.495672] system 00:08: iomem range 0x100000-0x2fffffff could not be reserved
[    0.530438] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.530442] pci 0000:00:01.0:   IO window: disabled
[    0.530449] pci 0000:00:01.0:   MEM window: 0xfaa00000-0xfeafffff
[    0.530454] pci 0000:00:01.0:   PREFETCH window: 0x000000bff00000-0x000000dfefffff
[    0.530474] pci 0000:00:01.0: setting latency timer to 64
[    0.530479] bus: 00 index 0 io port: [0x00-0xffff]
[    0.530482] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.530485] bus: 01 index 0 mmio: [0x0-0x0]
[    0.530487] bus: 01 index 1 mmio: [0xfaa00000-0xfeafffff]
[    0.530490] bus: 01 index 2 mmio: [0xbff00000-0xdfefffff]
[    0.530492] bus: 01 index 3 mmio: [0x0-0x0]
[    0.530501] NET: Registered protocol family 2
[    0.532019] Switched to high resolution mode on CPU 0
[    0.532685] Switched to high resolution mode on CPU 1
[    0.544086] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.544518] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.545248] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.545749] TCP: Hash tables configured (established 131072 bind 65536)
[    0.545753] TCP reno registered
[    0.552132] NET: Registered protocol family 1
[    0.552319] checking if image is initramfs... it is
[    1.155700] Freeing initrd memory: 7365k freed
[    1.156009] cpufreq: No nForce2 chipset.
[    1.156229] audit: initializing netlink socket (disabled)
[    1.156278] type=2000 audit(1246027621.156:1): initialized
[    1.165030] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.166728] VFS: Disk quotas dquot_6.5.1
[    1.166811] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.167675] fuse init (API version 7.10)
[    1.167791] msgmni has been set to 1498
[    1.168072] alg: No test for stdrng (krng)
[    1.168106] io scheduler noop registered
[    1.168109] io scheduler anticipatory registered
[    1.168111] io scheduler deadline registered
[    1.168130] io scheduler cfq registered (default)
[    1.168150] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.168245] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    1.168272] pci 0000:01:00.0: Boot video device
[    1.173039] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.173053] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.173235] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.173239] ACPI: Power Button (FF) [PWRF]
[    1.173313] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.173317] ACPI: Power Button (CM) [PWRB]
[    1.173795] processor ACPI_CPU:00: registered as cooling_device0
[    1.173948] processor ACPI_CPU:01: registered as cooling_device1
[    1.177769] isapnp: Scanning for PnP cards...
[    1.528510] Clocksource tsc unstable (delta = 2327909071 ns)
[    1.529480] isapnp: No Plug & Play device found
[    1.536677] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.538044] brd: module loaded
[    1.538515] loop: module loaded
[    1.538607] Fixed MDIO Bus: probed
[    1.538615] PPP generic driver version 2.4.2
[    1.538697] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.538736] Driver 'sd' needs updating - please use bus_type methods
[    1.538749] Driver 'sr' needs updating - please use bus_type methods
[    1.538929] sata_via 0000:00:0f.0: version 2.4
[    1.538954] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.539014] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.539130] scsi0 : sata_via
[    1.539264] scsi1 : sata_via
[    1.539316] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 20
[    1.539320] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 20
[    1.740024] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.952021] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.962757] pata_via 0000:00:0f.1: version 0.3.3
[    1.962770] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.962994] scsi2 : pata_via
[    1.963093] scsi3 : pata_via
[    1.966345] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    1.966348] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    2.164198] ata3.00: ATA-7: ST3160212A, 2AAA, max UDMA/100
[    2.164202] ata3.00: 312581808 sectors, multi 16: LBA48 
[    2.164456] ata3.01: ATA-4: ST36421A, 8.01, max UDMA/66
[    2.164459] ata3.01: 12596850 sectors, multi 16: LBA 
[    2.238872] ata3.00: configured for UDMA/100
[    2.252475] ata3.01: configured for UDMA/66
[    2.491185] ata4.00: ATA-5: MAXTOR 4K020H1, A08.1500, max UDMA/100
[    2.491189] ata4.00: 39876480 sectors, multi 16: LBA 
[    2.491231] ata4.01: ATAPI: TSSTcorpCD/DVDW SH-W162Z, TS00, max UDMA/33
[    2.491262] ata4.00: limited to UDMA/33 due to 40-wire cable
[    2.504628] ata4.00: configured for UDMA/33
[    2.560282] ata4.01: configured for UDMA/33
[    2.561890] scsi 2:0:0:0: Direct-Access     ATA      ST3160212A       2AAA PQ: 0 ANSI: 5
[    2.562018] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.562043] sd 2:0:0:0: [sda] Write Protect is off
[    2.562046] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.562085] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.562178] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.562200] sd 2:0:0:0: [sda] Write Protect is off
[    2.562203] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.562240] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.562245]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.613566] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.613627] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.613750] scsi 2:0:1:0: Direct-Access     ATA      ST36421A         8.01 PQ: 0 ANSI: 5
[    2.613869] sd 2:0:1:0: [sdb] 12596850 512-byte hardware sectors: (6.44 GB/6.00 GiB)
[    2.613891] sd 2:0:1:0: [sdb] Write Protect is off
[    2.613895] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.613933] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.614003] sd 2:0:1:0: [sdb] 12596850 512-byte hardware sectors: (6.44 GB/6.00 GiB)
[    2.614025] sd 2:0:1:0: [sdb] Write Protect is off
[    2.614028] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.614065] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.614070]  sdb: sdb1 sdb2 < sdb5 >
[    2.664078] sd 2:0:1:0: [sdb] Attached SCSI disk
[    2.664127] sd 2:0:1:0: Attached scsi generic sg1 type 0
[    2.664217] scsi 3:0:0:0: Direct-Access     ATA      MAXTOR 4K020H1   A08. PQ: 0 ANSI: 5
[    2.664332] sd 3:0:0:0: [sdc] 39876480 512-byte hardware sectors: (20.4 GB/19.0 GiB)
[    2.664354] sd 3:0:0:0: [sdc] Write Protect is off
[    2.664357] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.664396] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.664465] sd 3:0:0:0: [sdc] 39876480 512-byte hardware sectors: (20.4 GB/19.0 GiB)
[    2.664486] sd 3:0:0:0: [sdc] Write Protect is off
[    2.664490] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.664540] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.664547]  sdc: sdc1
[    2.671242] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.671298] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.672381] scsi 3:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-W162Z TS00 PQ: 0 ANSI: 5
[    2.681871] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.681876] Uniform CD-ROM driver Revision: 3.20
[    2.681994] sr 3:0:1:0: Attached scsi CD-ROM sr0
[    2.682043] sr 3:0:1:0: Attached scsi generic sg3 type 5
[    2.682248] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.682279] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    2.682311] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    2.682401] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    2.682483] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfebff800
[    2.692016] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    2.692114] usb usb1: configuration #1 chosen from 1 choice
[    2.692168] hub 1-0:1.0: USB hub found
[    2.692183] hub 1-0:1.0: 8 ports detected
[    2.692319] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.692339] uhci_hcd: USB Universal Host Controller Interface driver
[    2.692370] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.692379] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.692441] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    2.692464] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000c400
[    2.692582] usb usb2: configuration #1 chosen from 1 choice
[    2.692616] hub 2-0:1.0: USB hub found
[    2.692630] hub 2-0:1.0: 2 ports detected
[    2.692739] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.692752] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.692810] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    2.692833] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000c800
[    2.692936] usb usb3: configuration #1 chosen from 1 choice
[    2.692969] hub 3-0:1.0: USB hub found
[    2.692980] hub 3-0:1.0: 2 ports detected
[    2.693088] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.693095] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    2.693150] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    2.693173] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000cc00
[    2.693278] usb usb4: configuration #1 chosen from 1 choice
[    2.693311] hub 4-0:1.0: USB hub found
[    2.693324] hub 4-0:1.0: 2 ports detected
[    2.693436] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.693449] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    2.693508] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    2.693531] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d000
[    2.693637] usb usb5: configuration #1 chosen from 1 choice
[    2.693670] hub 5-0:1.0: USB hub found
[    2.693681] hub 5-0:1.0: 2 ports detected
[    2.693842] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.693845] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.693974] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.696061] mice: PS/2 mouse device common for all mice
[    2.708099] rtc_cmos 00:02: RTC can wake from S4
[    2.708146] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.708202] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    2.708278] device-mapper: uevent: version 1.0.3
[    2.708421] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.708576] device-mapper: multipath: version 1.0.5 loaded
[    2.708581] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.708709] EISA: Probing bus 0 at eisa.0
[    2.708753] EISA: Detected 0 cards.
[    2.708840] cpuidle: using governor ladder
[    2.708844] cpuidle: using governor menu
[    2.709520] TCP cubic registered
[    2.709622] NET: Registered protocol family 10
[    2.710250] lo: Disabled Privacy Extensions
[    2.710714] NET: Registered protocol family 17
[    2.710743] Bluetooth: L2CAP ver 2.11
[    2.710746] Bluetooth: L2CAP socket layer initialized
[    2.710750] Bluetooth: SCO (Voice Link) ver 0.6
[    2.710752] Bluetooth: SCO socket layer initialized
[    2.710801] Bluetooth: RFCOMM socket layer initialized
[    2.710816] Bluetooth: RFCOMM TTY layer initialized
[    2.710820] Bluetooth: RFCOMM ver 1.10
[    2.710898] Using IPI No-Shortcut mode
[    2.710997] registered taskstats version 1
[    2.711146]   Magic number: 13:673:789
[    2.711262] rtc_cmos 00:02: setting system clock to 2009-06-26 14:47:03 UTC (1246027623)
[    2.711267] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.711269] EDD information not available.
[    2.711961] Freeing unused kernel memory: 532k freed
[    2.712132] Write protecting the kernel text: 4112k
[    2.712192] Write protecting the kernel read-only data: 1524k
[    2.730448] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.008693] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    3.063189] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.063294] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.064710] eth0: VIA Rhine II at 0xfebffc00, 00:13:8f:72:7f:6f, IRQ 23.
[    3.065424] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    3.304918] usb 1-2: configuration #1 chosen from 1 choice
[    3.768039] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    3.946065] usb 3-1: configuration #1 chosen from 1 choice
[    3.956026] usbcore: registered new interface driver hiddev
[    3.956157] usbcore: registered new interface driver usbhid
[    3.956164] usbhid: v2.6:USB HID core driver
[    3.985043] input: GreenAsia Inc.    USB Joystick      as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input4
[    3.985836] pantherlord 0003:0E8F:0003.0001: input,hidraw0: USB HID v1.10 Joystick [GreenAsia Inc.    USB Joystick     ] on usb-0000:00:10.1-1/input0
[    3.985855] pantherlord 0003:0E8F:0003.0001: Force feedback for PantherLord/GreenAsia devices by Anssi Hannula <anssi.hannula@gmail.com>
[    4.188039] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    4.346425] usb 4-1: configuration #1 chosen from 1 choice
[    4.545138] PM: Starting manual resume from disk
[    4.545143] PM: Resume from partition 8:21
[    4.545145] PM: Checking hibernation image.
[    4.545441] PM: Resume from disk failed.
[    4.588030] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    4.614250] kjournald starting.  Commit interval 5 seconds
[    4.614263] EXT3-fs: mounted filesystem with ordered data mode.
[    4.756804] usb 5-1: configuration #1 chosen from 1 choice
[    4.775056] input: USB Optical Mouse as /devices/pci0000:00/0000:00:10.3/usb5/5-1/5-1:1.0/input/input5
[    4.775203] generic-usb 0003:15CA:00C3.0002: input,hidraw1: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:10.3-1/input0
[   16.168603] udev: starting version 141
[   16.877836] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   17.273074] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.507744] cfg80211: Calling CRDA to update world regulatory domain
[   17.682843] Linux agpgart interface v0.103
[   18.560984] agpgart: Detected VIA VT3314 chipset
[   18.579873] agpgart-via 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   18.829599] cfg80211: World regulatory domain updated:
[   18.829605]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.829609]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.829612]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.829615]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.829618]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.829620]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.598554] nvidia: module license 'NVIDIA' taints kernel.
[   19.640331] Linux video capture interface: v2.00
[   19.854392] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.855228] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.10  Sat Jan 24 19:49:38 PST 2009
[   19.905025] gspca: main v2.3.0 registered
[   20.167886] gspca: probing 0c45:60b0
[   20.172057] gspca: probe ok
[   20.172077] gspca: probing 0c45:60b0
[   20.172095] gspca: probing 0c45:60b0
[   20.172137] usbcore: registered new interface driver sonixb
[   20.172186] sonixb: registered
[   20.602482] phy0: Selected rate control algorithm 'pid'
[   21.157407] Registered led device: rt73usb-phy0:radio
[   21.157452] Registered led device: rt73usb-phy0:assoc
[   21.157487] Registered led device: rt73usb-phy0:quality
[   21.157995] usbcore: registered new interface driver rt73usb
[   21.160960] usbcore: registered new interface driver snd-usb-audio
[   21.245682] C-Media PCI 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.485926] lp: driver loaded but no devices found
[   21.576363] Adding 321260k swap on /dev/sdb5.  Priority:-1 extents:1 across:321260k
[   22.122374] EXT3 FS on sdb1, internal journal
[   23.298198] NTFS driver 2.1.29 [Flags: R/O MODULE].
[   23.299874] NTFS-fs warning (device sdc1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   23.370198] NTFS volume version 3.1.
[   23.370621] NTFS-fs warning (device sda5): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   23.405424] NTFS volume version 3.1.
[   23.405667] NTFS-fs warning (device sda6): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   23.459399] NTFS volume version 3.1.
[   23.459642] NTFS-fs warning (device sda2): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   23.513889] NTFS volume version 3.1.
[   23.514134] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   23.550647] NTFS volume version 3.1.
[   23.849273] type=1505 audit(1246042044.636:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2121
[   23.901707] type=1505 audit(1246042044.688:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2125
[   23.901879] type=1505 audit(1246042044.688:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2125
[   23.901942] type=1505 audit(1246042044.688:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2125
[   23.901992] type=1505 audit(1246042044.688:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2125
[   30.294179] ppdev: user-space parallel port driver
[   32.569848] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   32.569873] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   32.569967] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   34.213401] eth0: link down
[   34.213671] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.215044] rt73usb 1-2:1.0: firmware: requesting rt73.bin
[   34.471331] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   60.855943] __ratelimit: 9 callbacks suppressed
[   71.616235] wlan0: authenticate with AP 00:23:f8:8b:0e:77
[   71.618001] wlan0: authenticated
[   71.618025] wlan0: associate with AP 00:23:f8:8b:0e:77
[   71.619855] wlan0: RX AssocResp from 00:23:f8:8b:0e:77 (capab=0x431 status=0 aid=1)
[   71.619878] wlan0: associated
[   71.631578] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   82.576025] wlan0: no IPv6 routers present
[  153.602372] __ratelimit: 5813 callbacks suppressed
[  158.604037] __ratelimit: 154921 callbacks suppressed


> **kamus said:**
> Que version del controlador para la tarjeta NVIDIA estas usando?

Saludos

La 96.

Salu1+1

---

### Post by kamus on 2009-06-26
Hey esa musica la tienes cargada en tu /home/usuario o la estas cargando directamente de la partición NTFS que tienes en tu disco? Si es así podrías intentar copiar algunos temas en tu home y reproducirlos desde esa ruta para ver los resultados (también un cat /etc/fstab podría ayudar a resolver ese detalle).

Saludos

---

### Post by Carlos C on 2009-06-26
Por favor escribe en el terminal:
```
sudo fdisk -l
```y también pega acá el contenido de tu archivo /etc/fstab.
Saludos.

Edito: jajaja Kamusin me ganó.

---

### Post by F.Y.N. on 2009-06-26
> **kamus said:**
> Hey esa musica la tienes cargada en tu /home/usuario o la estas cargando directamente de la partición NTFS que tienes en tu disco? Si es así podrías intentar copiar algunos temas en tu home y reproducirlos desde esa ruta para ver los resultados (también un cat /etc/fstab podría ayudar a resolver ese detalle).

Saludos

La tengo en "Mi música" de Windows, pero no creo que ese sea el problema, a veces el sistema se cae sin que no haga nada, de hecho cuando pegue el dmesg se me callo cuando sonó el, valga la redundancia, sonido del login.

> **Carlos C said:**
> Por favor escribe en el terminal:
```
sudo fdisk -l
```y también pega acá el contenido de tu archivo /etc/fstab.
Saludos.

Edito: jajaja Kamusin me ganó.

fdisk -l:

> Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x743f743f

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        3825    20482875    7  HPFS/NTFS
/dev/sda3            3826       19457   125564040    f  W95 Ext'd (LBA)
/dev/sda5            3826        8924    40957686    7  HPFS/NTFS
/dev/sda6            8925       19457    84606291    7  HPFS/NTFS

Disco /dev/sdb: 6449 MB, 6449587200 bytes
255 cabezas, 63 sectores/pista, 784 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xc7e5c7e5

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1         744     5976148+  83  Linux
/dev/sdb2             745         784      321300    5  Extendida
/dev/sdb5             745         784      321268+  82  Linux swap / Solaris

Disco /dev/sdc: 20.4 GB, 20416757760 bytes
255 cabezas, 63 sectores/pista, 2482 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x06580657

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1        2482    19936633+   7  HPFS/NTFSfstab:

> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=6b2976c3-2b4e-4e60-95be-af9806b0d049 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=8d77b85f-bfbe-48ad-942d-9832ea166d12 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda5 /media/Descargas ntfs umask=222,utf8 0 0

Ahora se me cae en el login, se queda pegado y tengo que reiniciar... me están entrando unas ganas de cambiarme de distro que ni te cuento....:(

Salu1+1

---

### Post by kamus on 2009-06-26
Te recomiendo instalar los ultimos controladores disponibles desde el sitio de nvidia ([http://www.nvidia.com/object/linux_display_ia32_185.18.14.html](http://www.nvidia.com/object/linux_display_ia32_185.18.14.html)) y deshabilitar los controladores que tienes instalado (controladores privativos).

La instalación en medianamente trivial, si necesitas ayuda puedes buscar en el mismo foro.

Saludos y cuenta como te fue ;)

---

### Post by F.Y.N. on 2009-06-27
Bueno, luego de que el sistema me empezara a andar peor opte por lo "sano" y reinstale ubuntu, ahora tengo los ultimos drivers de nvidia y ningún problema más, salvo el audio que se sigue cayendo igual que antes.

¿Que hago ahora?

---

### Post by Carlos C on 2009-06-28
Creo que acá tienes un problema:
> NTFS-fs warning (device sdc1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   23.370198] NTFS volume version 3.1.
[ 23.370621] NTFS-fs warning (device sda5): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   23.405424] NTFS volume version 3.1.
[ 23.405667] NTFS-fs warning (device sda6): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   23.459399] NTFS volume version 3.1.
[ 23.459642] NTFS-fs warning (device sda2): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   23.513889] NTFS volume version 3.1.
[ 23.514134] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   23.550647] NTFS volume version 3.1.Parece que tienes un problema a la hora de montar cada partición ntfs de tu disco sda. Mirando lo que pusiste de tu fstab:
> /dev/sda5 /media/Descargas ntfs umask=222,utf8 0 0Yo creo que debieras probar cambiando ligeramente esa linea:
```
/dev/sda5 /media/Descargas ntfs nls=utf8,umask=0222 0 0
```¿En cuál partición están los archivos de música que escuchas?

---

### Post by F.Y.N. on 2009-06-28
Ahora no tengo nada montado, como dije arriba, tuve que reinstalar.


Salu1+1

---

### Post by Carlos C on 2009-06-28
Ok, estamos hablando de un sistema limpio, eso lo entendí. Sin embargo los cuelgues siguen ocurriendo cuando reproduces archivos de audio, ¿no es así? ¿En qué partición están estos archivos de audio?

---

### Post by F.Y.N. on 2009-06-28
Ah... siguen estando donde mismo (descargas), pero ahora no instale el NTFS-3G ni NTFS-Config (que hacían que las particiones se montaran al inicio), esta "así nomas", por que no quiero tocar nada hasta que el maldito audio no se me caiga.

¿Quieres que ponga el contenido de algún archivo?

---

### Post by Carlos C on 2009-06-29
Lo que quiero saber es si ahora, mientras no montas esas particiones, sigues teniendo cuelgues.

---

### Post by F.Y.N. on 2009-06-30
**Si, se me cae igual.**

Hice la prueba copiando unas carpetas de música en un pendrive, y escuche de ahí; paso exactamente lo mismo: como a los 15 minutos, se quedo congelado y no pude hacer nada mas que reiniciarlo directo del botón.


Salu1+1

PD: Mods, saquen los tags de NTFS, porque ese no es el problema.

---

### Post by moreback on 2009-06-30
Yo ya estoy pensando que es un problema con el driver de video. Hay algún proceso que come demasiada memoria (eso explica el congelamiento de la máquina ya que el kernel pasa lo de la RAM a la swap) y puede ser el Xorg.

Veo compiz.real y emerald al mismo tiempo en tu listado de top, esto ya no es una instalación por defecto, no? que modificaciones hiciste?

---

### Post by F.Y.N. on 2009-06-30
> **moreback said:**
> Yo ya estoy pensando que es un problema con el driver de video. Hay algún proceso que come demasiada memoria (eso explica el congelamiento de la máquina ya que el kernel pasa lo de la RAM a la swap) y puede ser el Xorg.

_Veo compiz.real y emerald al mismo tiempo en tu listado de top_, esto ya no es una instalación por defecto, no? **que modificaciones hiciste?**

_Eso es antiguo, después del post 17 reinstale._

Ahora le puse el driver 186 (creo... porque ahora estoy en Windows ya que sin poder escuchar música me muero. Pero era el ultimo, eso estoy seguro), el Audacious, los paquetes Alsa-base y Alsa-oss, el compiz con un tema de emerald y... no recuerdo nada más, si de hecho, lo he usado re poco porque se cae siempre.


Salu1+1

---

### Post by F.Y.N. on 2009-07-04
Nada de nada????

---

### Post by Carlos C on 2009-07-04
Mira, puedes ver si tu problema se relaciona con lo que dicen acá:

[http://ayudaubuntu.com/2008/09/solucionado-el-problema-de-cuelgues-por-culpa-del-audio/](http://ayudaubuntu.com/2008/09/solucionado-el-problema-de-cuelgues-por-culpa-del-audio/)

---

### Post by F.Y.N. on 2009-07-06
> **Carlos C said:**
> Mira, puedes ver si tu problema se relaciona con lo que dicen acá:

[http://ayudaubuntu.com/2008/09/solucionado-el-problema-de-cuelgues-por-culpa-del-audio/](http://ayudaubuntu.com/2008/09/solucionado-el-problema-de-cuelgues-por-culpa-del-audio/)
Instale el paquete ese (que ahora se lama algo de "flash-extrasound") pero la cosa sigue igual, es más, ni si quiera abrí el navegador la ultima vez y se cayo como a los 10 minutos sin poder hacer nada.


Salu1+1

---

### Post by repunante on 2010-03-10
Buenas,

Ya hace tiempo que se abrió el tema y quizá ya se soluciono pero yo tuve hoy el mismo problema que comentáis con el sonido en Ubuntu 9.10 e investigando un poco parece que la mayoría de las tarjetas de sonido C-Media dan problemas en esta distribución (aunque también me daba problemas con Fedora 12).
Encontré [aquí]("http://ubuntuforums.org/showthread.php?t=1316102") una solución que de momento me esta funcionando. Esta en el segundo post, simplemente ejecutando en terminal:

sudo apt-get --purge remove pulseaudio && sudo apt-get install esound 


A ver si os sirve a vosotros también.

Suerte.

---

