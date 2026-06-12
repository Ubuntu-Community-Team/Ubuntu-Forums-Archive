---
title: "Focusrite 2i2 is a phantom (now in the right place i hope)"
date: 2015-01-17
forum: Hardware
---

### Post by heron2 on 2015-01-17
[(I already posted this thread]("http://ubuntuforums.org/showthread.php?t=2261157"), but i realized that the section was the wrong one, so i posted it again here, if a moderator notices the double, i kindly ask him to delete the one in the wrong section and let live this one here)

Hi everyone, i'm a total newbie of ubuntu/linux.
I have a problem: i produce music, and i want to try out linux. I  installed Ubuntu Studio. The problem is: i connected my ext. audio card  to the computer (a focusrite scarlett 2i2) but the audio keeps coming  out from the computer's hardware.
[I followed this tutoria]("http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack")l, but nothing, nothing comes out from the audio card and it keeps coming from the laptop itself. What's going on? Did it happen to you too?

If it's kind of usefull, my computer is an Hp Compaq 6910p (not the best).
Thanks in advance! :popcorn:

---

### Post by heron2 on 2015-01-17
I just ran qtljack, and now it sends error messages, this is what happened in the message box:
 
 [COLOR=#999999]22:21:38.782 Patchbay disattivato.[/COLOR]
 [COLOR=#999999]22:21:38.785 Resetta le statistiche.[/COLOR]
 [COLOR=#cccc99]22:21:38.796 Connessioni di ALSA cambiate.[/COLOR]
 [COLOR=#999999]22:21:38.816 D-BUS: Servizio disponibile (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = File o directory non esistente
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]22:21:38.863 Cambiamento nel grafico delle connessioni di ALSA.[/COLOR]
 (qjackctl:9819): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:9819): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:9819): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:9819): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]22:24:24.296 D-BUS: il server JACK non può essere avviato. Mi dispiace[/COLOR]
 Cannot connect to server socket err = File o directory non esistente
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl:9819): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:9819): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 Sat Jan 17 22:24:24 2015: Starting jack server...
 Sat Jan 17 22:24:24 2015: JACK server starting in realtime mode with priority 10
 Sat Jan 17 22:24:24 2015: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio1": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio1
 Sat Jan 17 22:24:24 2015: ERROR: Failed to acquire device name : Audio1 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio1
 Sat Jan 17 22:24:24 2015: ERROR: Audio device hw:1 cannot be acquired...
 Sat Jan 17 22:24:24 2015: ERROR: Cannot initialize driver
 Sat Jan 17 22:24:24 2015: ERROR: JackServer::Open failed with -1
 Sat Jan 17 22:24:24 2015: ERROR: Failed to open server
 Sat Jan 17 22:24:25 2015: Saving settings to "/home/filippo/.config/jack/conf.xml" ...
 (qjackctl:9819): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:9819): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]22:24:31.777 Non sono riuscito ad avviare JACK come client. - Operazione fallita. - Impossibile connettersi al server JACK. Controlla la finestra dei messaggi per maggiori informazioni.[/COLOR]
 Cannot connect to server socket err = File o directory non esistente
 Cannot connect to server request channel
 jack server is not running or cannot be started

What does it mean? what am i supposed to do?

---

