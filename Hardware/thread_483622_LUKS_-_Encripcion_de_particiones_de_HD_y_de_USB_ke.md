---
title: "LUKS - Encripcion de particiones de HD y de USB keys - mini guia"
date: 2007-06-24
forum: Hardware
---

### Post by ariel on 2007-06-24
Hace poco me decidi a encriptar el disco en la laptop linux del laburo y en mi casa. Y de paso tambien los USB keys y USB-HD que uso para llevar archivos y hacer backups. El tema encripcion de particiones en linux se simplifico muchisimo ultimamente.

Lo que sigue es mi resumen de varios howtos que consulte para hacer andar esto. 
Uso LUKS/Dm-Crypt (linux unified key setup). No encripte el filesystem (particion montada en "/")  ni el swap ni /home, solo otras particiones (ejemplo: /media/mis_archivos) que uso todos los dias y donde esta la info que me interesaba proteger. Usando PAM, las particiones encriptadas hace 'automount' cuando me logeo al sistema. 

Al conectar un USB key encriptado, gnome lo detecta (bueno, el kernel lo detecta) y muestra una ventanita pidiendo la clave para abrirlo. super cool. Tambien encontre drivers  para montar particiones LUKS encriptadas desde winXP, funcionaron ok.

Todo esto te da la seguridad de que nadie puede acceder a tus archivos sin tu clave. 

Lo que sigue no pretende ser un howto (ni ahi), pero puede darte una idea de como llegar. Si estas probando, tene cuidado de no tocar las particiones que contienen "/" (filesystem), swap, /home. Cuidado... un error jugando con las particiones puede hacer que pierdas tu informacion o que tu linux no bootee mas, asi que, ojo, no digas que no te adverti :)

Nota: particiones de HD que fueron encriptadas y no removidas ("commented out") en /etc/fstab, hacen que el proceso de booteo se interrumpa para pedir la clave. Feisty tiene un bug conocido, se olvidaron de poner el prompt ("ingrese la clave"), y el proceso de booteo parece detenerse con un prompt de linea de comando. Tipea ctrl-c, despues "reboot", y el proceso continua con la carga de gnome como siempre. 

Ciao!



   - [Intrepid / 8.10] - **Encrypt an HD partition (not the root or /home) with LUKS and have it automount upon login**
        - sdaXX is the partition to be encrypted
        - Move existing data out of the partition to be encrypted (existing data in the partition will be erased)
        - sudo umount /dev/sdaXX (may require 'sudo su')
        - Comment out the partition's entry line in /etc/fstab
        - sudo apt-get install cryptsetup hashalot libpam-mount
        - Load the required modules[INDENT]       sudo modprobe aes
      sudo modprobe dm-crypt
      sudo modprobe dm-mod
[/INDENT][INDENT]- Add the three modules above to /etc/modules
[/INDENT]- Optional: Overwrite exisiting data, if paranoid:[INDENT]       - !!Cuidado... sobreescribe la particion: sudo badblocks -c 10240 -s -w -t random -v /dev/sdaXX
      - if super paranoid (*very* slow): dd if=/dev/urandom of=/dev/sdaXX
[/INDENT]- Create an encrypted filesystem in /dev/sdaXX and make sure you use the same password as your login password (for PAM automount):[INDENT]                        sudo luksformat -t ext3 /dev/sdaXX
[/INDENT]- Mount the cryptdisk and give it to the user (e.g ariel):[INDENT]       sudo cryptsetup luksOpen /dev/sdaXX sdaXXdisk
                       mount /dev/mapper/sdaXXdisk /media/sdaXX
                       sudo chown -R ariel:ariel /media/sdaXX
                       sudo umount /media/sdaXX
                       sudo cryptsetup luksClose sdaXXdisk
[/INDENT]- Manual Mounting (no PAM)[INDENT]       sudo cryptsetup luksOpen /dev/sda7 sda7disk
[/INDENT][INDENT]                             - after execution, the new deviceMapper will be auto-mounted by the kernel, and gnome will prompt for the LUKS volume password
[/INDENT][INDENT]         (for this to occur, there should be *no entry* in /etc/fstab for this partition)
[/INDENT]- Automount on Login via PAM:[INDENT]                     - Add an entry for your user in /etc/security/pam_mount.conf.xml   - close to the end of the file, right before the "</pam_mount>" line :
[/INDENT][INDENT][INDENT]<volume fstype="crypt" path="/dev/sdaXX" mountpoint="/media/sdaXX" options="cipher=aes" />

(add one line entry for each encrypted partition)

[/INDENT][/INDENT][INDENT]                     - Edit /etc/pam.d/(login|gdm): (only need to do this once, for the first encrypted & automounted partition)
[/INDENT][INDENT][INDENT]                                  sudo echo "@include common-pammount" >> /etc/pam.d/login
                                 sudo echo "@include common-pammount" >> /etc/pam.d/gdm
[/INDENT][/INDENT]- To add a password (up to 8 are supported):[INDENT]                    cryptsetup luksAddKey /dev/sdaXX
[/INDENT]- LUKS/DM-Crypt[INDENT]                 - Howto with in-place conversion: [https://help.ubuntu.com/community/EncryptedFilesystemHowto7](https://help.ubuntu.com/community/EncryptedFilesystemHowto7)

                - Windows Drivers[INDENT]                           - [http://www.freeotfe.org/](http://www.freeotfe.org/)
                          - [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)[/INDENT][/INDENT]

---

### Post by Thalskarth on 2008-11-14
Hola, alguien sabe si esta info sigue siendo valida para intrepid? No quisiera ponerme a probarlo y que falle algo...

gracias

---

### Post by majatu on 2008-11-14
> **Thalskarth said:**
> Hola, alguien sabe si esta info sigue siendo valida para intrepid? No quisiera ponerme a probarlo y que falle algo...

gracias

Muy interesante! pregunto lo mismo, funcionara en intrepid? si anda, estaria bueno que valla a CoMo's en la web de Ubuntu-Ar no?

saludos!

---

### Post by ariel on 2008-11-15
> **majatu said:**
> Muy interesante! pregunto lo mismo, funcionara en intrepid? si anda, estaria bueno que valla a CoMo's en la web de Ubuntu-Ar no?

saludos!


Recien actualize el minihowto para Intrepid. De hecho la unica parte que cambia es la de "Automount on Login via PAM".

Yo uso particiones encriptadas con LUKS desde hace dos anios, en casa y en el trabajo. Al hacer upgrades de Ubuntu, lo unico que hay que retocar es "/etc/security/pam_mount.conf.xml", siguiendo las instrucciones.

---

### Post by Thalskarth on 2008-11-17
Te hago una consulta...

llegado el caso de que cree una partición encriptada.
y luego, en el futuro reinstale el SO, deberia hacer los mismos pasos, pero evitando el formateo de la particion en cuestión? 
para asi poder volver a tener acceso a ella???

gracias

---

### Post by ariel on 2008-11-17
> **Thalskarth said:**
> Te hago una consulta...

llegado el caso de que cree una partición encriptada.
y luego, en el futuro reinstale el SO, deberia hacer los mismos pasos, pero evitando el formateo de la particion en cuestión? 
para asi poder volver a tener acceso a ella???

gracias

No... si haces un update regular de ubuntu, lo unico que necesitas re-hacer es la primer parte del paso "Automount via PAM":

```
- Automount on Login via PAM:[INDENT] - Add an entry for your user in /etc/security/pam_mount.conf.xml - close to the end of the file, right before the "</pam_mount>" line :
[/INDENT]<volume fstype="crypt" path="/dev/sdaXX" mountpoint="/media/sdaXX" options="cipher=aes" />

(add one line entry for each encrypted partition)
```

Si haces un fresh install (desde cero), tenes que hace el paso "Automount via PAM" completo.

Al dejar el root filesystem (/) y los home folders sin encriptar, los updates o full fresh installs son faciles, la maquina siempre bootea bien; una vez terminada la instalacion tenes que volver a activar las particiones encriptadas, porque ubuntu no las puede detectar; en gparted salen como "Unknown".

Obviamente, si te decidis a intentar esto, tenes que tener mucho cuidado, hacer un backup de tus cosas antes de empezar etc.

---

### Post by Thalskarth on 2008-11-18
ahh... ok, gracias...


si mi idea, luego del backup, probarlo en una partición usando datos no importantes a fin de aprender sin muchos riesgos

y luego, cuando le tome la mano, si pasar la info que vale la pena :)

gracias


PD: Mi objetivo principal es aprender :lolflag:

---

