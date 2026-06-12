---
title: "Problemas con drivers de NVIDIA después de compilar kernel"
date: 2010-11-30
forum: Hardware
---

### Post by ChirmiPlay on 2010-11-30
Hola a todos. Tengo un problema: compilé e instalé el kernel 2.6.36.1 en Ubuntu 10.10 de 64 bits (no activé módulos raros ni nada), y al reiniciar la PC y elegir el nuevo kernel en el Grub, aparece el logo de Ubuntu cargándose. Se carga en su totalidad pero luego se congela el Sistema y no muestra nada más que el logo. Traté de reinstalar los drivers privativos de NVIDIA que tenía, iniciando en modo de recuperación. Al instalarlo, me aparece un mensaje diciendo que hubo un error con el módulo del kernel de NVIDIA (algo así) y por eso no se puede instalar. ¿Qué debo hacer? Gracias.

PD: Probé compilando con distintos métodos, pero siempre sucede lo mismo.

---

### Post by guillermolisi on 2010-11-30
La instalacion de drivers de Nvidia, la version que se obtiene de su website, no deben ser instalados en modo recuperacion. De hecho cuando se intenta tal cosa sale un cartel avisando que de continuar se corre el riesgo que algunas cosas dejen de funcionar.

Para poder hacer una correcta instalacion (de los drivers bajados del website de Nvidia) se debe iniciar en modo normal, matar el servicio GDM/KDM (segun se use Gnome o KDE) y proceder a instalar con las instrucciones que salen en pantalla cuando se ejecuta el instalador bajado.

---

### Post by EnriqueK on 2010-12-01
NO tenés que borrar la carpeta de fuentes que usaste para compilar, ya se que pesa mucho, pero al menos es la solución que encontré ya que al parecer el Linux headers que se crea no es suficiente para compilar los módulos de nvidia.
Lo que te recomiendo es que instales el controlador nvidia desde los repositorios, y además instalar el paquete "dkms" de esta manera te olvidas del asunto por que si lo instalás usanado el NVIDIA  ..run , cada vez que haya un cambio del kernel, del xorg y de otros que no recuerfo, vas a tener que repetir el proceso de desinstalar y volver a instalar el controlador nvidia
En mi instalación de Debian siempre instalé entrando en recovery mode y nunca tuve problemas.
No creo que sea necesario recompilar , bastaría con tener  la carpeta de sources descomprimida en /usr/src

---

