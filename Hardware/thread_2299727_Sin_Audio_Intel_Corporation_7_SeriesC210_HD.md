---
title: "Sin Audio Intel Corporation 7 Series/C210 HD"
date: 2015-10-20
forum: Hardware
---

### Post by Mauri_Bataleon on 2015-10-20
Hola. Instalé Ubuntu 15.04 y no tuve audio. Actualicé al Kernel 4.2.3 y tampoco. Instalé el Ubuntu 14.04 y tampoco.
Mi información ALSA es la siguiente: [http://www.alsa-project.org/db/?f=82603c4aef59f560b8a0f0a4680402db76d110fb](http://www.alsa-project.org/db/?f=82603c4aef59f560b8a0f0a4680402db76d110fb)
Espero su ayuda. Desde ya muchas gracias!!

---

### Post by Yellow Pasque on 2015-10-21
Quite la línea de código que agregó. No va a ayudar.
```
snd_hda_intel: model=generic
```

Instale la última módulo de sonido:
```
sudo apt-get install dkms
cd ~/
wget https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-lts-vivid-dkms_0.201509251531%7Eubuntu14.04.1_all.deb
sudo dpkg -i oem-audio-hda-daily-lts-vivid-dkms_0.201509251531~ubuntu14.04.1_all.deb
```

Reinicie el sistema y compruebe que el volumen no está silenciado:
```
alsamixer
```

Si aún no tiene sonido, le sugiero la presentación de un informe de error.
```
ubuntu-bug audio
```

---

### Post by Mauri_Bataleon on 2015-10-22
Muchísimas gracias [**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594")!
Hoy prendí la computadora para continuar mi lucha, y me encontré con la sorpresa de tener sonido.
Sinceramente no se como se solucionó, pudo haber sido por alguno de los métodos de este foro que estuve probando, o simplemente las actualizaciones del sistema me activaron el sonido como correspondía (Ubuntu recientemente instalado).
Sólo se activó para los parlantes de la computadora, y no para auriculares, entonces modifiqué *snd_hda_intel: model=generic* por: *snd_hda_intel: model=auto* y ahora tengo sonido completo.
Otra vez gracias por dedicarle tiempo a mi problema!!

---

