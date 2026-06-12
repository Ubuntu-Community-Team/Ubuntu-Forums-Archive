---
title: "None of my jabber clients work"
date: 2008-09-02
forum: General Help
---

### Post by resonantfreq on 2008-09-02
It seems there is an error with sasl, but I have not been able to find it.

pidgin -d reports:

...
(15:51:13) sasl: Mechs found: GSSAPI 
(15:51:13) sasl: No worthy mechs found

psi reports:

simplesasl.cpp: No mechanism available

gajim:

Traceback (most recent call last):
  File "/usr/share/gajim/src/common/xmpp/idlequeue.py", line 132, in process_events
    obj.pollin()
  File "/usr/share/gajim/src/common/xmpp/transports_nb.py", line 153, in pollin
    self._do_receive() 
  File "/usr/share/gajim/src/common/xmpp/transports_nb.py", line 255, in _do_receive
    self.on_receive(received)
  File "/usr/share/gajim/src/common/xmpp/client_nb.py", line 161, in _on_receive_stream_features
    self.on_stream_start()
  File "/usr/share/gajim/src/common/xmpp/client_nb.py", line 203, in _on_tcp_stream_start
    self._is_connected()
  File "/usr/share/gajim/src/common/xmpp/client_nb.py", line 186, in _is_connected
    self.on_connect(self, self.connected)
  File "/usr/share/gajim/src/common/connection.py", line 425, in _connect_success
    self._register_handlers(con, con_type)
  File "/usr/share/gajim/src/common/connection.py", line 436, in _register_handlers
    con.auth(name, self.password, self.server_resource, 1, self.__on_auth)
  File "/usr/share/gajim/src/common/xmpp/client_nb.py", line 227, in auth
    self.get_attrs(self._on_doc_attrs)
  File "/usr/share/gajim/src/common/xmpp/client_nb.py", line 117, in get_attrs
    self.onreceive(self._on_receive_document_attrs)
  File "/usr/share/gajim/src/common/xmpp/transports_nb.py", line 211, in onreceive
    if not recv_handler(None) and _tmp == self.on_receive:
  File "/usr/share/gajim/src/common/xmpp/client_nb.py", line 146, in _on_receive_document_attrs
    self.onreceive(self._on_receive_stream_features)
  File "/usr/share/gajim/src/common/xmpp/transports_nb.py", line 211, in onreceive
    if not recv_handler(None) and _tmp == self.on_receive:
  File "/usr/share/gajim/src/common/xmpp/client_nb.py", line 161, in _on_receive_stream_features
    self.on_stream_start()
  File "/usr/share/gajim/src/common/xmpp/client_nb.py", line 246, in _on_doc_attrs
    self.SASL.auth()
AttributeError: NonBlockingClient instance has no attribute 'SASL'

TIA.

---

