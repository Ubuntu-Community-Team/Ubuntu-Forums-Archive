---
title: "WP8060U en Intrepid Ibex"
date: 2008-11-17
forum: Hardware
---

### Post by Afkael on 2008-11-17
Hola Gente, no uso ubuntu pero quise ayudar a un amigo que se compró esta tableta gráfica a quiere instalarla en su ubuntu intrepid ibex.
Estamos siguiendo esta guia: [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html) pero a pesar de ser bastante sencilla no nos ha funcionado..
Lo que me pregunto es si se debe modificar el xorg.conf, yo supongo que si pero no encuentro nada al respecto.
A la tableta la reconoce, ya que puede hacer "click" con ella pero no mueve ningún puntero..
Yo soy usuario de Gentoo pero mi xorg.conf tiene muchas más secciones, la suya no tiene mouse ni keyboards y la verdá yo también soy bastabte noob en linux como para sacarlo del paso.

Espero puedan ayudarme. Gracias.

---

### Post by guillermolisi on 2008-11-18
El asunto es que en II hubo profundos cambios en X11. La mayor parte de los parametros que se definian a nivel del xorg.conf ahora estan a nivel del server X, por eso practicamente no encontras nada comparado inclusive con la 8.04.

Por casualidad, no guardaron una copia del xorg.conf anterior, como para probar con el nuevo xorg.conf de II ?

La otra alternativa es instalar 8.04 en lugar de la 8.10 y ver que pasa, si es que aun no lo han hecho.

---

### Post by Hei Ku on 2008-11-18
Primero que nada, estaria bueno ver que chipset usa y demas.

Si es usb, que corra el lsusb, si es pci, lspci. Postea el resultado y seguimos viendo.

---

### Post by Afkael on 2008-11-24
Disculpen la demora pero me retracé en conseguir la data.. no podia dar con mi compadre, pero bue.. esto dice lsusb:

> Bus 001 Device 005: ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet

esta es la tableta:
[http://www.geniusnet.com:80/geniusOnline/online.portal?_nfpb=true&productPortlet_actionOverride=%2Fportlets%2FproductArea%2Fproduct%2FquerySection&_windowLabel=productPortlet&productPortletproductId=210856&productPortletsectionId=210858&_pageLabel=productPage&test=portlet-action](http://www.geniusnet.com:80/geniusOnline/online.portal?_nfpb=true&productPortlet_actionOverride=%2Fportlets%2FproductArea%2Fproduct%2FquerySection&_windowLabel=productPortlet&productPortletproductId=210856&productPortletsectionId=210858&_pageLabel=productPage&test=portlet-action)

y tiene esta mobo(M2N-X -NVIDIA® nForce&#8482; 520&#8482; MCP-):
[http://www.asus.com/products.aspx?l1=3&l2=101&l3=499&model=1576&modelmenu=1](http://www.asus.com/products.aspx?l1=3&l2=101&l3=499&model=1576&modelmenu=1)

No se que otra infotmación les sea útil.. estoy a su disposición. Gracias

---

