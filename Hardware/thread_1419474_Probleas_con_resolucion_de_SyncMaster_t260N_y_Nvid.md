---
title: "Probleas con resolucion de SyncMaster t260N y Nvidia"
date: 2010-03-01
forum: Hardware
---

### Post by bronto64 on 2010-03-01
Hola no puedo configurar bien la resolución del monitor, edite el xorg.config y nada, en la pagina de samsung no hay drivers para linux. Tengo el citado monitor y una Nvidia 8600gt . Alguien me podria guiar por donde ir toqueteando, la resolución que uso hoy es de 1600x1200, pero quiero usar la nativa del monitor, ya que sino tengo que configurarla cada vez que entro (no se porque no guarda la configuracion, debo activar los privilegios de admin antes de tocar? ).
Gracias.
Federico.

---

### Post by guillermolisi on 2010-03-02
> **bronto64 said:**
> Hola no puedo configurar bien la resolución del monitor, edite el xorg.config y nada, en la pagina de samsung no hay drivers para linux. Tengo el citado monitor y una Nvidia 8600gt . Alguien me podria guiar por donde ir toqueteando, la resolución que uso hoy es de 1600x1200, pero quiero usar la nativa del monitor, ya que sino tengo que configurarla cada vez que entro (no se porque no guarda la configuracion, debo activar los privilegios de admin antes de tocar? ).
Gracias.
Federico.
Si estas utilizando nvidia-settings para configurar el video, invocalo con "sudo" para que te permita guardar las modificaciones que realizas.
```
sudo nvidia-settings
``` en una consola/terminal y deberia guardarte los cambios para la proxima sesion.

---

