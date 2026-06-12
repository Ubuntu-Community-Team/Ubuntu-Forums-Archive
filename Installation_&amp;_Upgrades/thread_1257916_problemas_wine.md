---
title: "problemas wine"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by martin1717 on 2009-09-04
hola, como les va? lñes cuento mi problema. tengo q instalar el pspice, en mi compu con ubuntu. es una aplicacion de simulacion de circuitos q necesito si o si para la facultad y el laburo, y no quiero usar alternativas porq es el unico simulador de circuitos, q cuando lo exigis sigue estando muy cerca de la realidad. como es una aplicacion para windows tengo q usar el wine. yo lo instale el pspice, y lo abre bien, pero no tengo ningun componente disponible para colocar en el circuito. yo supongo q el wine no puede leer las librerias de componetes. alguien sabe como puedo hacer para q las lea? o no se tal vez el problema es otro. por favor, ayudenme, no quiero tener q usar una compu con windows o hacer una particion en la mia para poder usarlo. Gracias de antemano

---

### Post by martin1717 on 2009-09-04
hola, como les va? I tell them my problem. I have to install pspice, in my compu with ubuntu. is a circuit simulation application or if I need if for the faculty and laburo, and do not want to use alternatives because it is the only circuit simulator that time it was still very close to reality. as is a Windows application I use the wine. pspice install and open fine, but I have no place available for electronic component in the circuit. I suppose the wine can not read libraries, components. anyone know how I can do for you to read? or not perhaps the problem lies elsewhere. Please help me, I do not have to use a computer with windows or make a partition in order to use mine. Thanks in advance

---

### Post by joelgsf on 2009-09-07
Martin,

If your components are in DLL's you can tell Wine to use them (see Wine ---> Configure Wine ---> Libraries). Otherwise, or if nothing else works, I would sugest you to install a Virtual Machine (e.g. Virtual Box) and install Windows in it. Then install pspice as a regular installation for Windows.
Hope it helps!

---

### Post by brian3 on 2009-09-07
hi  change to virtualbox  no problems there

---

### Post by martin1717 on 2009-09-07
elegi virtualbox. funciona perfecto. 
Gracias!!!

---

