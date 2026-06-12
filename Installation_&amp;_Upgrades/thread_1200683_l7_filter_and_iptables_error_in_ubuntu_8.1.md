---
title: "l7 filter and iptables error in ubuntu 8.1"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by furiac3lta on 2009-06-30
Hi i need your help please. I try to install l7 filter in ubuntu 8.10 intrepid ibex with kernel 2.6.27-7-generic and iptables version 1.4.0. I read a manual that i find in jpcozar qos page and it tell i must follow this steps:
 
> 
 
**Layer7**
 
**L7-filter kernel**
 
wget [http://downloads.sourceforge.net/l7-filter/netfilter-layer7-v2.20.tar.gz](http://downloads.sourceforge.net/l7-filter/netfilter-layer7-v2.20.tar.gz)
**L7-filter userpace**
 
wget [http://downloads.sourceforge.net/l7-filter/l7-filter-userspace-0.10.tar.gz](http://downloads.sourceforge.net/l7-filter/l7-filter-userspace-0.10.tar.gz)
**L7 descarga de definiciones de protocolos**
 
wget [http://downloads.sourceforge.net/l7-filter/l7-protocols-2008-12-18.tar.gz](http://downloads.sourceforge.net/l7-filter/l7-protocols-2008-12-18.tar.gz)
**Iptables**
 
**Descarga de Iptables (versión 1.4.2)**
 
wget [http://www.netfilter.org/projects/iptables/files/iptables-1.4.2.tar.bz2](http://www.netfilter.org/projects/iptables/files/iptables-1.4.2.tar.bz2)
**Kernel 2.6.27.7**
 
**Descarga del kernel**
 
sudo apt-get install linux-source
**Parcheo y recompilación del kernel**
 
**Instalar l7-filter y los fuentes del kernel**
 
tar -xvf /usr/src/linux-source-2.6.27.tar.bz2ln -s /usr/src/linux-source-2.6.27 /usr/src/linuxtar -xvf netfilter-layer7-v2.20.tar.gz
**Aplicar el parche a las fuentes del kernel**
 
cd /usr/src/linuxpatch -p1 < ../netfilter-layer7-v2.20/kernel-2.6.25-layer7-2.20.patch
**Aplicar el parche e instalar Iptables 1.4.2**
 
tar -xvf iptables-1.4.2.tar.bz2cd iptables-1.4.2patch -p1 < ../netfilter-layer7-v2.20/iptables-1.4-for-kernel-2.6.20forward-layer7-2.20.patchchmod +x extensions/.layer7-testmake KERNEL_DIR=/usr/src/linuxmake install KERNEL_DIR=/usr/src/linux
**********************************
 
Well ....when i try to compile iptables 1.4.2 with "make KERNEL_DIR=/usr/src/linux "
the pc show me this error:
 
> 
[SIZE=2]root@marcelo-laptop:/usr/src/iptables-1.4.2# make KERNEL_DIR=/usr/src/linux[/SIZE]
[SIZE=2]make all-recursive[/SIZE]
[SIZE=2]make[1]: se ingresa al directorio `/usr/src/iptables-1.4.2'[/SIZE]
[SIZE=2]Making all in extensions[/SIZE]
[SIZE=2]make[2]: se ingresa al directorio `/usr/src/iptables-1.4.2/extensions'[/SIZE]
[SIZE=2]GEN initext4.c[/SIZE]
[SIZE=2]CC initext4.o[/SIZE]
[SIZE=2]AR libext4.a[/SIZE]
[SIZE=2]GEN initext6.c[/SIZE]
[SIZE=2]CC initext6.o[/SIZE]
[SIZE=2]AR libext6.a[/SIZE]
[SIZE=2]GEN matches4.man[/SIZE]
[SIZE=2]GEN matches6.man[/SIZE]
[SIZE=2]GEN targets4.man[/SIZE]
[SIZE=2]GEN targets6.man[/SIZE]
[SIZE=2]CC libxt_CLASSIFY.oo[/SIZE]
[SIZE=2]CCLD libxt_CLASSIFY.so[/SIZE]
[SIZE=2]CC libxt_comment.oo[/SIZE]
[SIZE=2]CCLD libxt_comment.so[/SIZE]
[SIZE=2]CC libxt_connbytes.oo[/SIZE]
[SIZE=2]CCLD libxt_connbytes.so[/SIZE]
[SIZE=2]CC libxt_connlimit.oo[/SIZE]
[SIZE=2]CCLD libxt_connlimit.so[/SIZE]
[SIZE=2]CC libxt_connmark.oo[/SIZE]
[SIZE=2]CCLD libxt_connmark.so[/SIZE]
[SIZE=2]CC libxt_CONNMARK.oo[/SIZE]
[SIZE=2]CCLD libxt_CONNMARK.so[/SIZE]
[SIZE=2]CC libxt_CONNSECMARK.oo[/SIZE]
[SIZE=2]CCLD libxt_CONNSECMARK.so[/SIZE]
[SIZE=2]CC libxt_conntrack.oo[/SIZE]
[SIZE=2]CCLD libxt_conntrack.so[/SIZE]
[SIZE=2]CC libxt_dccp.oo[/SIZE]
[SIZE=2]CCLD libxt_dccp.so[/SIZE]
[SIZE=2]CC libxt_dscp.oo[/SIZE]
[SIZE=2]CCLD libxt_dscp.so[/SIZE]
[SIZE=2]CC libxt_DSCP.oo[/SIZE]
[SIZE=2]CCLD libxt_DSCP.so[/SIZE]
[SIZE=2]CC libxt_esp.oo[/SIZE]
[SIZE=2]CCLD libxt_esp.so[/SIZE]
[SIZE=2]CC libxt_hashlimit.oo[/SIZE]
[SIZE=2]CCLD libxt_hashlimit.so[/SIZE]
[SIZE=2]CC libxt_helper.oo[/SIZE]
[SIZE=2]CCLD libxt_helper.so[/SIZE]
[SIZE=2]CC libxt_iprange.oo[/SIZE]
[SIZE=2]CCLD libxt_iprange.so[/SIZE]
[SIZE=2]CC libxt_length.oo[/SIZE]
[SIZE=2]CCLD libxt_length.so[/SIZE]
[SIZE=2]CC libxt_limit.oo[/SIZE]
[SIZE=2]CCLD libxt_limit.so[/SIZE]
[SIZE=2]CC libxt_mac.oo[/SIZE]
[SIZE=2]CCLD libxt_mac.so[/SIZE]
[SIZE=2]CC libxt_mark.oo[/SIZE]
[SIZE=2]CCLD libxt_mark.so[/SIZE]
[SIZE=2]CC libxt_MARK.oo[/SIZE]
[SIZE=2]CCLD libxt_MARK.so[/SIZE]
[SIZE=2]CC libxt_multiport.oo[/SIZE]
[SIZE=2]CCLD libxt_multiport.so[/SIZE]
[SIZE=2]CC libxt_NFLOG.oo[/SIZE]
[SIZE=2]CCLD libxt_NFLOG.so[/SIZE]
[SIZE=2]CC libxt_NFQUEUE.oo[/SIZE]
[SIZE=2]CCLD libxt_NFQUEUE.so[/SIZE]
[SIZE=2]CC libxt_NOTRACK.oo[/SIZE]
[SIZE=2]CCLD libxt_NOTRACK.so[/SIZE]
[SIZE=2]CC libxt_owner.oo[/SIZE]
[SIZE=2]libxt_owner.c: En la funciÃ³n â€˜owner_mt_print_item_v0â€™:[/SIZE]
[SIZE=2]libxt_owner.c:327: aviso: el formato no es una cadena literal y no tiene argumentos de formato[/SIZE]
[SIZE=2]libxt_owner.c: En la funciÃ³n â€˜owner_mt6_print_item_v0â€™:[/SIZE]
[SIZE=2]libxt_owner.c:378: aviso: el formato no es una cadena literal y no tiene argumentos de formato[/SIZE]
[SIZE=2]CCLD libxt_owner.so[/SIZE]
[SIZE=2]CC libxt_physdev.oo[/SIZE]
[SIZE=2]CCLD libxt_physdev.so[/SIZE]
[SIZE=2]CC libxt_pkttype.oo[/SIZE]
[SIZE=2]CCLD libxt_pkttype.so[/SIZE]
[SIZE=2]CC libxt_quota.oo[/SIZE]
[SIZE=2]CCLD libxt_quota.so[/SIZE]
[SIZE=2]CC libxt_rateest.oo[/SIZE]
[SIZE=2]CCLD libxt_rateest.so[/SIZE]
[SIZE=2]CC libxt_RATEEST.oo[/SIZE]
[SIZE=2]CCLD libxt_RATEEST.so[/SIZE]
[SIZE=2]CC libxt_sctp.oo[/SIZE]
[SIZE=2]CCLD libxt_sctp.so[/SIZE]
[SIZE=2]CC libxt_SECMARK.oo[/SIZE]
[SIZE=2]CCLD libxt_SECMARK.so[/SIZE]
[SIZE=2]CC libxt_standard.oo[/SIZE]
[SIZE=2]CCLD libxt_standard.so[/SIZE]
[SIZE=2]CC libxt_state.oo[/SIZE]
[SIZE=2]CCLD libxt_state.so[/SIZE]
[SIZE=2]CC libxt_statistic.oo[/SIZE]
[SIZE=2]CCLD libxt_statistic.so[/SIZE]
[SIZE=2]CC libxt_string.oo[/SIZE]
[SIZE=2]CCLD libxt_string.so[/SIZE]
[SIZE=2]CC libxt_tcp.oo[/SIZE]
[SIZE=2]CCLD libxt_tcp.so[/SIZE]
[SIZE=2]CC libxt_tcpmss.oo[/SIZE]
[SIZE=2]CCLD libxt_tcpmss.so[/SIZE]
[SIZE=2]CC libxt_TCPMSS.oo[/SIZE]
[SIZE=2]CCLD libxt_TCPMSS.so[/SIZE]
[SIZE=2]CC libxt_TCPOPTSTRIP.oo[/SIZE]
[SIZE=2]CCLD libxt_TCPOPTSTRIP.so[/SIZE]
[SIZE=2]CC libxt_time.oo[/SIZE]
[SIZE=2]CCLD libxt_time.so[/SIZE]
[SIZE=2]CC libxt_tos.oo[/SIZE]
[SIZE=2]CCLD libxt_tos.so[/SIZE]
[SIZE=2]CC libxt_TOS.oo[/SIZE]
[SIZE=2]CCLD libxt_TOS.so[/SIZE]
[SIZE=2]CC libxt_TRACE.oo[/SIZE]
[SIZE=2]CCLD libxt_TRACE.so[/SIZE]
[SIZE=2]CC libxt_u32.oo[/SIZE]
[SIZE=2]CCLD libxt_u32.so[/SIZE]
[SIZE=2]CC libxt_udp.oo[/SIZE]
[SIZE=2]CCLD libxt_udp.so[/SIZE]
[SIZE=2]CC libipt_addrtype.oo[/SIZE]
[SIZE=2]CCLD libipt_addrtype.so[/SIZE]
[SIZE=2]CC libipt_ah.oo[/SIZE]
[SIZE=2]CCLD libipt_ah.so[/SIZE]
[SIZE=2]CC libipt_CLUSTERIP.oo[/SIZE]
[SIZE=2]CCLD libipt_CLUSTERIP.so[/SIZE]
[SIZE=2]CC libipt_DNAT.oo[/SIZE]
[SIZE=2]CCLD libipt_DNAT.so[/SIZE]
[SIZE=2]CC libipt_ecn.oo[/SIZE]
[SIZE=2]CCLD libipt_ecn.so[/SIZE]
[SIZE=2]CC libipt_ECN.oo[/SIZE]
[SIZE=2]CCLD libipt_ECN.so[/SIZE]
[SIZE=2]CC libipt_icmp.oo[/SIZE]
[SIZE=2]CCLD libipt_icmp.so[/SIZE]
[SIZE=2]CC libipt_layer7.oo[/SIZE]
[SIZE=2]libipt_layer7.c:27:39: aviso: linux/netfilter/xt_layer7.h: No existe el fichero Ã³ directorio[/SIZE]
[SIZE=2]libipt_layer7.c: En la funciÃ³n â€˜helpâ€™:[/SIZE]
[SIZE=2]libipt_layer7.c:41: error: â€˜IPTABLES_VERSIONâ€™ no se declarÃ³ aquÃ (primer uso en esta funciÃ³n)[/SIZE]
[SIZE=2]libipt_layer7.c:41: error: (Cada identificador no declarado solamente se reporta una vez[/SIZE]
[SIZE=2]libipt_layer7.c:41: error: para cada funcion en la que aparece.)[/SIZE]
[SIZE=2]libipt_layer7.c: En el nivel principal:[/SIZE]
[SIZE=2]libipt_layer7.c:52: aviso: se declarÃ³ â€˜struct xt_layer7_infoâ€™ dentro de la lista de parÃ¡metros[/SIZE]
[SIZE=2]libipt_layer7.c:52: aviso: su Ã¡mbito es solamente esta definiciÃ³n o declaraciÃ³n, lo cual probablemente no es lo que desea[/SIZE]
[SIZE=2]libipt_layer7.c:52: aviso: no hay un prototipo previo para â€˜parse_protocol_fileâ€™[/SIZE]
[SIZE=2]libipt_layer7.c: En la funciÃ³n â€˜parse_protocol_fileâ€™:[/SIZE]
[SIZE=2]libipt_layer7.c:55: aviso: la declaraciÃ³n de â€˜lineâ€™ oscurece a una declaraciÃ³n global[/SIZE]
[SIZE=2]../include/iptables.h:16: aviso: aquÃ estÃ¡ la declaraciÃ³n oscurecida[/SIZE]
[SIZE=2]libipt_layer7.c:96: error: â€˜MAX_PROTOCOL_LENâ€™ no se declarÃ³ aquÃ (primer uso en esta funciÃ³n)[/SIZE]
[SIZE=2]libipt_layer7.c:99: error: puntero deferenciado a tipo de dato incompleto[/SIZE]
[SIZE=2]libipt_layer7.c:105: error: â€˜MAX_PATTERN_LENâ€™ no se declarÃ³ aquÃ (primer uso en esta funciÃ³n)[/SIZE]
[SIZE=2]libipt_layer7.c:107: error: puntero deferenciado a tipo de dato incompleto[/SIZE]
[SIZE=2]libipt_layer7.c: En la funciÃ³n â€˜pre_processâ€™:[/SIZE]
[SIZE=2]libipt_layer7.c:152: aviso: la declaraciÃ³n de â€˜rindexâ€™ oscurece a una declaraciÃ³n global[/SIZE]
[SIZE=2]/usr/include/string.h:313: aviso: aquÃ estÃ¡ la declaraciÃ³n oscurecida[/SIZE]
[SIZE=2]libipt_layer7.c: En el nivel principal:[/SIZE]
[SIZE=2]libipt_layer7.c:205: aviso: no hay un prototipo previo para â€˜readl7dirâ€™[/SIZE]
[SIZE=2]libipt_layer7.c:260: aviso: se declarÃ³ â€˜struct xt_layer7_infoâ€™ dentro de la lista de parÃ¡metros[/SIZE]
[SIZE=2]libipt_layer7.c: En la funciÃ³n â€˜parse_layer7_protocolâ€™:[/SIZE]
[SIZE=2]libipt_layer7.c:287: aviso: se pasa el argumento 3 de â€˜parse_protocol_fileâ€™ desde un tipo de puntero incompatible[/SIZE]
[SIZE=2]libipt_layer7.c:305: error: puntero deferenciado a tipo de dato incompleto[/SIZE]
[SIZE=2]libipt_layer7.c:305: error: puntero deferenciado a tipo de dato incompleto[/SIZE]
[SIZE=2]libipt_layer7.c:305: error: â€˜MAX_PATTERN_LENâ€™ no se declarÃ³ aquÃ (primer uso en esta funciÃ³n)[/SIZE]
[SIZE=2]libipt_layer7.c: En la funciÃ³n â€˜parseâ€™:[/SIZE]
[SIZE=2]libipt_layer7.c:318: aviso: se pasa el argumento 2 de â€˜parse_layer7_protocolâ€™ desde un tipo de puntero incompatible[/SIZE]
[SIZE=2]libipt_layer7.c:320: error: puntero deferenciado a tipo de dato incompleto[/SIZE]
[SIZE=2]libipt_layer7.c: En la funciÃ³n â€˜printâ€™:[/SIZE]
[SIZE=2]libipt_layer7.c:365: error: puntero deferenciado a tipo de dato incompleto[/SIZE]
[SIZE=2]libipt_layer7.c:366: error: puntero deferenciado a tipo de dato incompleto[/SIZE]
[SIZE=2]libipt_layer7.c: En la funciÃ³n â€˜saveâ€™:[/SIZE]
[SIZE=2]libipt_layer7.c:374: error: puntero deferenciado a tipo de dato incompleto[/SIZE]
[SIZE=2]libipt_layer7.c:374: error: puntero deferenciado a tipo de dato incompleto[/SIZE]
[SIZE=2]libipt_layer7.c: En el nivel principal:[/SIZE]
[SIZE=2]libipt_layer7.c:377: error: la variable â€˜layer7â€™ tiene inicializador pero de tipo de dato incompleto[/SIZE]
[SIZE=2]libipt_layer7.c:378: error: se especificÃ³ el campo desconocido â€˜nameâ€™ en el inicializador[/SIZE]
[SIZE=2]libipt_layer7.c:378: aviso: exceso de elementos en el inicializador de struct[/SIZE]
[SIZE=2]libipt_layer7.c:378: aviso: (cerca de la inicializaciÃ³n de â€˜layer7â€™)[/SIZE]
[SIZE=2]libipt_layer7.c:379: error: se especificÃ³ el campo desconocido â€˜versionâ€™ en el inicializador[/SIZE]
[SIZE=2]libipt_layer7.c:379: error: â€˜IPTABLES_VERSIONâ€™ no se declarÃ³ aquÃ (no en una funciÃ³n)[/SIZE]
[SIZE=2]libipt_layer7.c:379: aviso: exceso de elementos en el inicializador de struct[/SIZE]
[SIZE=2]libipt_layer7.c:379: aviso: (cerca de la inicializaciÃ³n de â€˜layer7â€™)[/SIZE]
[SIZE=2]libipt_layer7.c:380: error: se especificÃ³ el campo desconocido â€˜sizeâ€™ en el inicializador[/SIZE]
[SIZE=2]libipt_layer7.c:380: error: aplicaciÃ³n invÃ¡lida de â€˜sizeofâ€™ a un tipo de dato incompleto â€˜struct xt_layer7_infoâ€™ [/SIZE]
[SIZE=2]libipt_layer7.c:380: aviso: exceso de elementos en el inicializador de struct[/SIZE]
[SIZE=2]libipt_layer7.c:380: aviso: (cerca de la inicializaciÃ³n de â€˜layer7â€™)[/SIZE]
[SIZE=2]libipt_layer7.c:381: error: se especificÃ³ el campo desconocido â€˜userspacesizeâ€™ en el inicializador[/SIZE]
[SIZE=2]libipt_layer7.c:381: error: aplicaciÃ³n invÃ¡lida de â€˜sizeofâ€™ a un tipo de dato incompleto â€˜struct xt_layer7_infoâ€™ [/SIZE]
[SIZE=2]libipt_layer7.c:381: aviso: exceso de elementos en el inicializador de struct[/SIZE]
[SIZE=2]libipt_layer7.c:381: aviso: (cerca de la inicializaciÃ³n de â€˜layer7â€™)[/SIZE]
[SIZE=2]libipt_layer7.c:382: error: se especificÃ³ el campo desconocido â€˜helpâ€™ en el inicializador[/SIZE]
[SIZE=2]libipt_layer7.c:382: aviso: exceso de elementos en el inicializador de struct[/SIZE]
[SIZE=2]libipt_layer7.c:382: aviso: (cerca de la inicializaciÃ³n de â€˜layer7â€™)[/SIZE]
[SIZE=2]libipt_layer7.c:383: error: se especificÃ³ el campo desconocido â€˜parseâ€™ en el inicializador[/SIZE]
[SIZE=2]libipt_layer7.c:383: aviso: exceso de elementos en el inicializador de struct[/SIZE]
[SIZE=2]libipt_layer7.c:383: aviso: (cerca de la inicializaciÃ³n de â€˜layer7â€™)[/SIZE]
[SIZE=2]libipt_layer7.c:384: error: se especificÃ³ el campo desconocido â€˜final_checkâ€™ en el inicializador[/SIZE]
[SIZE=2]libipt_layer7.c:384: aviso: exceso de elementos en el inicializador de struct[/SIZE]
[SIZE=2]libipt_layer7.c:384: aviso: (cerca de la inicializaciÃ³n de â€˜layer7â€™)[/SIZE]
[SIZE=2]libipt_layer7.c:385: error: se especificÃ³ el campo desconocido â€˜printâ€™ en el inicializador[/SIZE]
[SIZE=2]libipt_layer7.c:385: aviso: exceso de elementos en el inicializador de struct[/SIZE]
[SIZE=2]libipt_layer7.c:385: aviso: (cerca de la inicializaciÃ³n de â€˜layer7â€™)[/SIZE]
[SIZE=2]libipt_layer7.c:386: error: se especificÃ³ el campo desconocido â€˜saveâ€™ en el inicializador[/SIZE]
[SIZE=2]libipt_layer7.c:386: aviso: exceso de elementos en el inicializador de struct[/SIZE]
[SIZE=2]libipt_layer7.c:386: aviso: (cerca de la inicializaciÃ³n de â€˜layer7â€™)[/SIZE]
[SIZE=2]libipt_layer7.c:387: error: se especificÃ³ el campo desconocido â€˜extra_optsâ€™ en el inicializador[/SIZE]
[SIZE=2]libipt_layer7.c:388: aviso: exceso de elementos en el inicializador de struct[/SIZE]
[SIZE=2]libipt_layer7.c:388: aviso: (cerca de la inicializaciÃ³n de â€˜layer7â€™)[/SIZE]
[SIZE=2]libipt_layer7.c: En la funciÃ³n â€˜libipt_layer7_initâ€™:[/SIZE]
[SIZE=2]libipt_layer7.c:392: aviso: declaraciÃ³n implÃcita de la funciÃ³n â€˜register_matchâ€™[/SIZE]
[SIZE=2]make[2]: *** [libipt_layer7.oo] Error 1[/SIZE]
[SIZE=2]make[2]: se sale del directorio `/usr/src/iptables-1.4.2/extensions'[/SIZE]
[SIZE=2]make[1]: *** [all-recursive] Error 1[/SIZE]
[SIZE=2]make[1]: se sale del directorio `/usr/src/iptables-1.4.2'[/SIZE]
[SIZE=2]make: *** [all] Error 2[/SIZE]
[SIZE=2]root@marcelo-laptop:/usr/src/iptables-1.4.2# [/SIZE]

 
 
I´m wait for help. Thanks.

---

