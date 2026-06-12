---
title: "Me demora en reconocer la tarjeta de red R8168 Realtek"
date: 2013-10-19
forum: Hardware
---

### Post by Urkie on 2013-10-19
Amigos:

Amigos, hace rato que estoy intentando de que Ubuntu reconozca mi tarjeta de red. De Ubuntu 6.06 en adelante no me anda mi tarjeta Realtek R8168. He visto ya en los foros que tenian problemas similares, me he bajado hasta un script para solucionarlo y pero no dio resultado. Hasta ahora, pude hacerla andar instalando los drivers de la web de Realtek, pero con eso surgio otro inconveniente. Una vez instalado, paso entre 5 y 1o min. para reconocerla.
Ahora cada vez que inicio Ubuntu me aparece "Red cableada desconectada" y luego de unos 5 o 10 min. se conecta sola. Yo quisiera obviamente que ya se establezcla la conexion de entrada.

Datos:

 # lsmod | grep r8168
r8168                 261295  0 

lspci:
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)

Agradezco a todos los que me puedan ayudar con este problema.

Juan

---

