---
title: "Plasma crashed after an upgrade"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by carbonyc on 2009-10-17
Hi, I'm having this trouble with Plasma when I start my system:

-- Backtrace:
Application: Área de trabalho do Plasma (kdeinit4), signal: Segmentation fault
[Current thread is 0 (LWP 3659)]

Thread 2 (Thread 0xa923db90 (LWP 3660)):
#0  0xb7fb3430 in __kernel_vsyscall ()
#1  0xb64c90e5 in pthread_cond_wait@@GLIBC_2.3.2 () from
/lib/tls/i686/cmov/libpthread.so.0
#2  0xb66a92ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7db0172 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xb76ecac2 in ?? () from /usr/lib/libQtNetwork.so.4
#5  0xb7daf132 in ?? () from /usr/lib/libQtCore.so.4
#6  0xb64c54ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb669a49e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb5fd2a10 (LWP 3659)):
[KCrash Handler]
#6  0xb662f896 in memcpy () from /lib/tls/i686/cmov/libc.so.6
#7  0xbfcce554 in ?? ()
#8  0xa95d1f9d in ?? () from /usr/lib/libplasma_applet-system-monitor.so.4
#9  0xa95d359b in SM::Applet::connectToEngine () from
/usr/lib/libplasma_applet-system-monitor.so.4
#10 0xa95f9292 in ?? () from /usr/lib/kde4/plasma_applet_sm_hdd.so
#11 0xb5d5ed47 in Plasma::Corona::loadLayout () from /usr/lib/libplasma.so.3
#12 0xb5d60791 in Plasma::Corona::initializeLayout () from
/usr/lib/libplasma.so.3
#13 0xb4b39a5d in ?? () from /usr/lib/libkdeinit4_plasma.so
#14 0xb4b3a075 in ?? () from /usr/lib/libkdeinit4_plasma.so
#15 0xb4b3d5ab in ?? () from /usr/lib/libkdeinit4_plasma.so
#16 0xb7eb91b8 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#17 0xb7eb9e42 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#18 0xb7ebef77 in ?? () from /usr/lib/libQtCore.so.4
#19 0xb7ebf09c in ?? () from /usr/lib/libQtCore.so.4
#20 0xb7eb416f in QObject::event () from /usr/lib/libQtCore.so.4
#21 0xb695fd3c in QApplicationPrivate::notify_helper () from
/usr/lib/libQtGui.so.4
#22 0xb696803e in QApplication::notify () from /usr/lib/libQtGui.so.4
#23 0xb747049d in KApplication::notify () from /usr/lib/libkdeui.so.5
#24 0xb7ea3bcb in QCoreApplication::notifyInternal () from
/usr/lib/libQtCore.so.4
#25 0xb7ed2d51 in ?? () from /usr/lib/libQtCore.so.4
#26 0xb7ecf3a0 in ?? () from /usr/lib/libQtCore.so.4
#27 0xb6512b88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#28 0xb65160eb in ?? () from /usr/lib/libglib-2.0.so.0
#29 0xb6516268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#30 0xb7ecf2f8 in QEventDispatcherGlib::processEvents () from
/usr/lib/libQtCore.so.4
#31 0xb6a01a75 in ?? () from /usr/lib/libQtGui.so.4
#32 0xb7ea21fa in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#33 0xb7ea2642 in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#34 0xb7ea4ae9 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#35 0xb695fbb7 in QApplication::exec () from /usr/lib/libQtGui.so.4
#36 0xb4b25b56 in kdemain () from /usr/lib/libkdeinit4_plasma.so
#37 0x0804e27d in _start ()

Unfortunately it happened after an upgrade I've made, and seems to be a problem from a kubuntu-ppa repository.
There's a dependency problem in my system, started after the last upgrade I tried to do, that is blocking my synaptics. Thus I can't upgrade or install any package, or even remove.
The problem is between plasma-widgets-addons and plasmoid-weather-extragear packages.
This the exit from terminal, when I do "apt-get install -f" to correct the dependencies:


carbonyc@carbonyc-desktop ~ $ sudo apt-get install -f
[sudo] password for carbonyc:
Lendo listas de pacotes... Pronto
Construindo árvore de dependências
Lendo informação de estado... Pronto
Corrigindo dependências... Pronto
Os seguintes pacotes foram automaticamente instalados e não são mais requeridos:
  libqt4-scripttools
Use 'apt-get autoremove' para removê-los.
Os pacotes extra a seguir serão instalados:
  plasma-widgets-addons
Os NOVOS pacotes a seguir serão instalados:
  plasma-widgets-addons
0 pacotes atualizados, 1 pacotes novos instalados, 0 a serem removidos e 108 não atualizados.
1 pacotes não totalmente instalados ou removidos.
É preciso baixar 0B/1499kB de arquivos.
Depois desta operação, 3965kB adicionais de espaço em disco serão usados.
Você quer continuar [S/n]? s
AVISO: Os pacotes a seguir não podem ser autenticados!
  plasma-widgets-addons
Aviso de autenticação sobreposto.
(Lendo banco de dados ... 173290 arquivos e diretórios atualmente instalados).
Desempacotando plasma-widgets-addons (de .../plasma-widgets-addons_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb) ...
dpkg: erro processando /var/cache/apt/archives/plasma-widgets-addons_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb (--unpack):
 tentando sobrescrever '/usr/share/kde4/apps/desktoptheme/default/weather/wind-arrows.svgz', que também está no pacote plasmoid-weather-extragear
dpkg-deb: sub-processo paste foi morto por sinal (Pipe quebrado)
Erros foram encontrados durante o processamento de:
 /var/cache/apt/archives/plasma-widgets-addons_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Sorry about the language, I'm brazilian. =)
So, what can I do about it?

---

