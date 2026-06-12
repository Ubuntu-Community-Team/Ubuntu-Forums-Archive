---
title: "no puedo imprimir alta calidad con hp p2055dn"
date: 2010-12-22
forum: Hardware
---

### Post by cseljatib on 2010-12-22
estimados colegas,
uso ubuntu 10.04 por anhos, y tengo una impresora hp laserjet P2055dn, pero no la puedo hacer imprimir en la mejor calidad a pesar de que lo defino en sus propiedades etc

la impresora funciona bien [su calidad alta] si envio un documento desde windows, y yo no tengo problemas para instalarla [la uso wireless, pero esta en red] y usarla, pero solo me permite imprimir en una calidad basica, aunque defina en printing mode= high quality, etc

he revisado varios posts, incluso este [http://ubuntuforums.org/showthread.php?t=1527516](http://ubuntuforums.org/showthread.php?t=1527516), que dice instala la impresora con  
$sudo hp-setup
pero aun no me sigue funcionando en calidad alta, a pesar de que seleccione esa opcion

alguien me puede ayudar por favor?

mil gracias desde ya

---

### Post by RafaelG on 2010-12-22
Por lo que comentas en tu problema con la impresora HP creo que esta mas orientado al driver y la version que estas utilizando. Puede que estes utilizando una version antigua y por ese motivo no te permite imprimir en Photo High quality

Ahora yo recuerdo que la ultima version que yo conoci hace un mes atras fue HPLIP 3.10.9, estuve tratando de ingresar a la pagina de HPLIP para verificar la informacion pero aparentemente se encuentra bajo mantencion por lo que me fue imposible confirmar cual versiones la que esta actualmente. 

De todas maneras te recomiendo recopilar informacion sobre el HPLIP que seria el driver para las impresoras HP en Ubuntu, yo actualmente estoy utilizando la version hplip 3.10.9 en Ubuntu 10.10 Mavrick modifique algunas cosas por que venia con algunos bugs pero nada complicado de solucionar asi que ahora mi HP trabaja al 100% en Ubuntu 10.10

Saludos,

---

### Post by cseljatib on 2010-12-22
rafael,
he bajado el ultimo hplip, lo he compilado incluso, usado distintas formas para instalarlo y aun no soy capaz de imprimir en la mejor calidad. Incluso intente con el codigo que aca indican [http://ubuntuforums.org/showthread.php?t=1645102](http://ubuntuforums.org/showthread.php?t=1645102) para 64bit [mi laptop es de 64bit]

lo otro que trate, solo por mientras, fue instalar mi impresora en mi virtual-machine [yo uso virtualbox], vale decir en windows, y desde ahi puedo imprimir en alta calidad. Claro esta esto es una solucion por mientras nada mas, pues no es la idea abrir la maquina virtual para imprimir lo que necesito.

que otro problema tendre??????

c

---

### Post by RafaelG on 2010-12-22
Cseljatib,


Podria postear lo que arroja tu terminal una vez ingresas sudo hp-setup. 

Saludos,

---

