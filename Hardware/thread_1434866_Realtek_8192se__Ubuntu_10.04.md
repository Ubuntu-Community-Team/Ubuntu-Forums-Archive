---
title: "Realtek 8192se  Ubuntu 10.04"
date: 2010-03-20
forum: Hardware
---

### Post by Mofall on 2010-03-20
Estimados,

   Hace poco compre una netbook Asus 1201t con una placa Wi fi Realtek 8192SE. Placa que Ubuntu no me reconocia, ni usando el ndiswrapper y el driver de windows.

   El tema lo solucione de esta manera:

  1- Baje el drvier de la pagina de Realtek

   [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2302](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2302)

  2- Descomprimi el Archivo

  3-Compilar el Codigo Fuente 
      sudo make

   4-Instalar el Driver en el Kernel
      make install

    5-Reiniciar
        reboot

    6- Copiar el Driver
    cp -rf firmware/RTL8192SE /lib/firmware           

    7- Cargar el Modulo en el Kernel
       sudo sh wlan0up

       ifconfig wlan0 up 


Estimados espero que les sea de utilidad. Ante cualquier duda, pueden ver el archivo del driver que tiene un readme.txt con data al respecto.

                             Saludos

---

