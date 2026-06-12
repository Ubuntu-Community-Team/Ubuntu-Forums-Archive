---
title: "Ubuntu me vacía la batería en 15 minutos"
date: 2009-11-17
forum: Hardware
---

### Post by nachocuervo on 2009-11-17
hola, instalé ubuntu por primera vez para poder sacar más provecho de mi notebook, pero resulta que cuando estoy corriendolo **la batería se descarga en pocos minutos (totalmente en 10 min),** hasta que la computadora se apaga súbitamente sin suspender ni nada se apaga y no se prende más. 
El comportamiento da la batería es muy raro porque parece descargarse incluso estando enchufada, si es que la enchufo cuando tiene bajo % de carga. No hice demasiadas pruebas porque no quiero romper nada, primero pregunto a ver si alguien puede guiarme, les adjunto dos archivos con info para aquel que sepa ayudarme.

[LIST]
[*]**La batería no está rota **porque bajo windows anda normalmente.
[/LIST]


[LIST]
[*]Tengo instalado **Wxp e instalé wubi, **creo q le llaman instalación virtual (sin particionar) aunque lo hice en otra partición diferente a winXP
[/LIST]
            [FONT=System][SIZE=1]Sistema operativo  [/SIZE][/FONT]
         [FONT=System][SIZE=1]Microsoft   Windows XP Home Edition 5.1.2600 (WinXP Retail) [/SIZE][/FONT]
             [FONT=System][SIZE=1] [/SIZE][/FONT]
         [FONT=System][SIZE=1] [/SIZE][/FONT]
         [FONT=System][SIZE=1]**Partizioni:**[/SIZE][/FONT] 
             [FONT=System][SIZE=1] [/SIZE][/FONT]
         [FONT=System][SIZE=1] [/SIZE][/FONT]
         [FONT=System][SIZE=1] [/SIZE][/FONT]
         [FONT=System][SIZE=1]C: (NTFS)  [/SIZE][/FONT]
         [FONT=System][SIZE=1]33385 MB (964 MB disponibili) [/SIZE][/FONT]
             [FONT=System][SIZE=1] [/SIZE][/FONT]
         [FONT=System][SIZE=1] [/SIZE][/FONT]
         [FONT=System][SIZE=1] [/SIZE][/FONT]
         [FONT=System][SIZE=1]D: (NTFS)  [/SIZE][/FONT]
         [FONT=System][SIZE=1]35777 MB (5921 MB disponibili) [/SIZE][/FONT]
             [FONT=System][SIZE=1]Tipo processore  [/SIZE][/FONT]
         [FONT=System][SIZE=1]Mobile Unknown, 1733 MHz (7.5 x 231) [/SIZE][/FONT]
             [FONT=System][SIZE=1] [/SIZE][/FONT]
         [FONT=System][SIZE=1]Memoria fisica: [/SIZE][/FONT]
             [FONT=System][SIZE=1] [/SIZE][/FONT]
         [FONT=System][SIZE=1] [/SIZE][/FONT]
         [FONT=System][SIZE=1]Totale  [/SIZE][/FONT]
         [FONT=System][SIZE=1]1014 MB [/SIZE][/FONT]
         
[LIST]
[*]ADJUNTO la información de hardware de la laptop en **1 report de AIDA32 (.doc)**
[/LIST]

[LIST]
[*]**y una "pantallazo" con el "histórico de la batería" **dps de 1 hora de usar ubuntu. 10 min con la batería y luego de eso la enchufe
[/LIST]


[LIST]
[*]Si alguien necesita que le diga algo más se lo digo con gusto, tengo tambien más pantallazos intermedios y de otros parámetros como voltaje por ej. quiero empezar a usar ubuntu pero me parece que asi se me rompre la batería!!!!
[/LIST]



[SIZE=1]*PD: espero no estar violando ninguna norma de este foro haciendo esta consulta, si así no es mi intención, busqué artículos sobre el tema por todos lados pero no encontre forma de entender que me pasa, ojalá pueda ayudarme alguien*[/SIZE]

---

### Post by guillermolisi on 2009-11-17
Me suena a que Ubuntu esta inciando sin reconocer las funciones ACPI de la motherboard, por eso no hay administracion de energia y puede ser tambien un factor que contribuya a ese consumo desmedido de la bateria.

Hay una forma de ver si se inicia con o sin ACPI pero para eso hay que operar sobre el Grub, cuando se inicia el SO.

---

