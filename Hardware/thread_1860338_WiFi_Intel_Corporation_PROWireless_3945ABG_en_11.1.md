---
title: "WiFi Intel Corporation PRO/Wireless 3945ABG en 11.10"
date: 2011-10-14
forum: Hardware
---

### Post by z37a on 2011-10-14
Gente, estoy buscando desesperado como hacer andar en 11.10 la placa de red Intel Corporation PRO/Wireless 3945ABG wifi de la notebook del trabajo, acabo de actualizar y dejo de funcionar! me dice que tengo el interruptor de hardware apagado o que el dispositivo no esta listo, lo malo es que justo es la del trabajo, y me quede sin wifi! Alguna idea, algún bug reportado?

---

### Post by z37a on 2011-10-14
Bien solucionado aparentemente, la solución es la siguiente según vi y la verdad en mi lógica carece de sentido:

```
sudo rmmod iwl3945 && sudo modprobe iwl3945
```

Si bien carece de sentido quitar y volver a poner el modulo del driver, probé de reiniciar y siguió funcionando!

---

