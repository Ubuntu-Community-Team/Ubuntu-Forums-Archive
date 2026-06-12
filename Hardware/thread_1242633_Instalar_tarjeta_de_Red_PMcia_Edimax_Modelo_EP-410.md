---
title: "Instalar tarjeta de Red PMcia Edimax Modelo EP-4103DL mara móbiles"
date: 2009-08-17
forum: Hardware
---

### Post by Roderick_Chile on 2009-08-17
Hola
Mi pregunta es la siguiente:
Instalé Xubuntu en mi Notebook de pocos recursos y solo podía tener puesta una tarjeta a la vez en las ranurasy dejé la de Wireless, pero ahora neesito instalar la de red... Cómo lo puedo hacer ya que no me la reconoce si la instalo?

Debo instalar un paquete especial o solo buscar drivers?

La tarjeta es una PMcia Edimax Modelo EP-4103DL mara móbiles

De antemano Gracias

---

### Post by Carlos C on 2009-08-22
Hola. A ver si entendí, tu problema es que te funciona la tarjeta pcmcia wifi, pero si la sacas y pones tu tarjeta pcmcia lan, entonces esta no anda correctamente, ¿es eso?

---

### Post by Patriciologico on 2009-08-31
> **Carlos C said:**
> Hola. A ver si entendí, tu problema es que te funciona la tarjeta pcmcia wifi, pero si la sacas y pones tu tarjeta pcmcia lan, entonces esta no anda correctamente, ¿es eso?

Entiendo que justamente eso es lo que le sucede.

En principio debiera correr el comando

```
lspci
```

Que nos mostrara efectivamente las tarjetas instaladas, que están reconocidas por el sistema.

Y pegar aquí el resultado.

Saludos!

---

