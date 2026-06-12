---
title: "Ubuntu 8.10 en notebook Compaq Presario CQ50-111la"
date: 2009-01-25
forum: Hardware
---

### Post by marianomocoroa on 2009-01-25
Acabo de comprar esta notebook y al instalarle ubuntu tuve que googlear varias horas hasta lograr hacer funcionar la placa wireless, finalmente la solucion lleva solo 5 minutos por lo que la posteo para que otro no tenga que dar tantas vueltas.

No utilizen los drivers restrictivos que intenta cargar para atheros, si buscan en google van a encontrar que les recomienda usar madwifi o ndiswrapper, tampoco. 

Esta solucion deberia funcionar para cualquier otra notebook con la misma placa para eso fijense en la salida del lspci

lspci | grep Ath
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

una vez eliminados los drivers restrictivos instalen lo sgte

# sudo apt-get install linux-backports-modules-$(uname -r)

reiniciar y listo wifi funcionando..

sino la levanta automaticamente prueben con 
sudo modprobe ath5k 
y si funciona lo agregan a /etc/modules para que se cargue al inicio

Lo que todavia no pude hacer funcionar son algunas de las hotkeys de la notebook, cuando lo logre posteo como, la placa de video una intel gma 500 maneja perfecto compiz con todos los efectos activados
Asi que si encuentran esta laptop en buen precio como me paso a mi comprenla tranquilos que es totalmente funcional con nuestro querido ubuntu

---

### Post by fuzzyworbles on 2009-02-16
no se como te puedo ayudar con los hotkeys, porque con mi cq50-116la, funcionan bien. pero dime eso: con tu lap, la puedes poner a standby (dormir)?

ah - y con wireless, te recemendo [http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers]("http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers") porque con eso se puede cambiar entre ath5k y madwifi con la heramienta 'athload' .. tambien ese modulo hace una senal mas podrioso que la que viene con ubuntu. con madwif y el modulo que viene con ubuntu se limete el txpower hasta 13dbm, pero con la que puede encontrar ariba, se va a 27dbm

disculpa mi espanol chafote.

---

### Post by Federicor on 2009-05-28
Hola que tal, recien instale el ubuntu 8.10 en mi presario pero no logro hacer andar la wireless, me podrian dar una manito con eso??
 
Gracias 
 
Federico

---

### Post by Federicor on 2009-05-28
Listo.. busque y encontre la solucion que copio a continuacion:
 
Ya tenia ratos de estar batallando con la wireless en mi laptop una compaq presario F755LA, ya que el manual que esta en la documentación de ubuntu no funciona para este modelo, me pase buscando en foros y blogs en los cuales daban soluciones, pero ninguna funcionaba o si funcionaba funcionaban mal, así que termine buscando en la pagina de madwifi, [[COLOR=#cccccc]http://madwifi.org[/COLOR]]("http://madwifi.org/") y al fin encontré un driver que me ha funcionado bien, hasta logre activar mi tarjeta en modo monitor (Ya tengo pa divertirme jejeje), bueno pues al grano, los pasos para activarla son:
Primero verificamos que sea la wifi sea la correcta para este driver tecleamos lo siguiente en una terminal:
lspci | grep Wireless
(Este comando nos devuelve el tipo de tarjeta Wireless reconocida por el sistema)
La terminal nos tendra que devolver algo como esto:
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
Si no les devuelve eso tengan por seguro que este tutorial no les va a funcionar [IMG]http://s.wordpress.com/wp-includes/images/smilies/icon_sad.gif[/IMG] , luego de eso tenemos que tener en cuenta que los controladores que trae ubuntu no funcionan así que no tenemos que tener instalados los siguientes paquetes para madwifi:
hostapd
madwifi-tools
Si tienen instalados esos paquetes desinstalenlos, ahora procedemos a descargar el driver, para ello nos dirigimos a [[COLOR=#cccccc]http://snapshots.madwifi-project.org/[/COLOR]]("http://snapshots.madwifi-project.org/") allí damos click en madwifi-hal-0.x.x.x donde las ultimas 3 X son numeros que van siendo actualizados con forme las nuevas verciones, en la proxima pagina le damos click al ultimo link que aparece en la lista, el cual contiene la ultima version del driver.
El archivo lo guardamos en el escritorio luego presionamos el juego de teclas alt+F2 y allí escribimos esto:
gnome-terminal
Con eso te abrirá una terminal, (es mas o menos como el cmd de windows), allí escribimos los siguientes comandos:
cd ~
(Ese comando nos ingresa al directorio home)
cd Escritorio
(Con ese comando ingresamos al Escritorio, si utilizan una version antigua de ubuntu el comando es cd Desktop)
tar xvzf madwifi-hal-xxxx.tar.gz
(Con este descomprimimos el archivo, las X las reemplazamos por la version que emos descargado, ejemplo:  tar xvzf madwifi-hal-0.10.5.6-r3861-20080903.tar.gz )
cd madwifi-hal-xxxx/
(con este ingresamos a lo que acabamos de descomprimir, volvemos a hacer el reemplazo de las “x”, ejemplo: cd madwifi-hal-0.10.5.6-r3861-20080903 )
make
(Con este comando compilamos el Driver)

sudo make install 
(Con este comando instalamos el driver)
Con esto ya tendremos compilado e instalado el driver, ahora procedemos a probarlo con el siguiente comando:
sudo modprobe ath_pci
Si** no** nos devuelve nada este comando vamos por buen camino [IMG]http://s.wordpress.com/wp-includes/images/smilies/icon_smile.gif[/IMG] así que procedemos a cargar los modulos para el arranque escribimos lo siguiente en la terminal:
sudo gedit /etc/modules
y al final del archivo agregamos las siguientes lineas:
#inicia configuracion de wireless
[I]ath_pci
#finaliza configuracion de wireless[/I]
Luego guardamos y procedemos a activar la tarjeta, con el siguiente comando, aunque lo mejor seria reiniciar:
sudo ifconfig ath0 up
(Si este comando les da algún error solo reinicien la PC con eso bastara)
Gracias igual 
 
Saludos
 
Federico

---

### Post by z37a on 2009-05-29
Con esa laptop no tenes problemas tambien con los drivers de video propietarios?

Creo que es la misma que tiene el usuario Cartos, va creo que se llama asi en el foro, y me acuerdo que ademas de tener problemas con el video tenia con la placa atheros, igualmnete te comento que ese equipo con el ubuntu 9.04 va a andar de 10 sin modificar nada! Te lo recomiendo como solucion rapida y facil.

---

### Post by fuzzyworbles on 2009-05-29
Estoy de acuerdo. Con 9.04, todos los dispositivos funcionen bien. Solamente tiene que descargar los modulos para nvidia (cq50-116L), pero ya esta integrado en ubuntu atraves jockey. aunque recientemente ath5k no funciona bien. el conexion esta lento y a veces se desconecta de repente. por eso, ahorra uso madwifi y se hala bien.

.. oh, y tambien tube que poner un opcion de kernel en grub para que se duerma.. pero el punto es que 9.04 apoya mas mi cq50-116L mas que 8.10.

---

### Post by juancarlospaco on 2009-05-29
***Instala 9.04 !*** :)

---

### Post by z37a on 2009-05-29
> **fuzzyworbles said:**
> Estoy de acuerdo. Con 9.04, todos los dispositivos funcionen bien. Solamente tiene que descargar los modulos para nvidia (cq50-116L), pero ya esta integrado en ubuntu atraves jockey. aunque recientemente ath5k no funciona bien. el conexion esta lento y a veces se desconecta de repente. por eso, ahorra uso madwifi y se hala bien.

.. oh, y tambien tube que poner un opcion de kernel en grub para que se duerma.. pero el punto es que 9.04 apoya mas mi cq50-116L mas que 8.10.

Mi atheros va de lujo con el ath5k, si noto mas lento que madwifi al conectar a la wifi al principio, pero en transferencia anda igual, ojo tengo una 5007, no se el resto que onda!!!!

---

### Post by Leandro17 on 2009-09-17
antes que nada perdon por resucitar el post...

bueno, tengo la misma notebook (cq50 111la) y me va excelente sin instalar nada con ubuntu jaunty... lo que no me gusta y no pude modificar, por eso lo pregunto, es que al apagar suena varias veces el pitido del sistema, ¿eso es normal o un error, como puedo solucionarlo o cambiarlo por algo mas tranqulizante?.. igual para cuando borro algo escrito y este llega al final... gracias de antemano...

---

