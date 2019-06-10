# Labs

## General: Windows Server

1. Crear VM de administración. Ésta VM es la única que debe tener acceso desde internet. Instalar herramientas RSAT.
2. Crear una VM Windows Server 2016 Core. Crear una arquitectura 1 Forest 1 Domain, será DC01. 
3. Crear una VM Windows Server 2016 Core, unirla al forest y agregarla como controlador de dominio, será DC02.
4. Modificar nombre de sitio y crear subnet correspondiente.
   * Hint: La subnet es que se creó en Azure.
5. Mover roles FSMO a DC02.
    * Hint: Verificar configuración NTP de ambos servers.
6. Realizar revisión y health check de plataforma, armar un informe. Usar herramientas integradas como tambien AD Replication status.
    * Importante: El informe tiene que incluir las siguientes configuraciones: NTP, Roles FSMO, configuración DNS en cada servidor, sitios y subnets. Para todos estos puntos, investigar las mejores prácticas de implementación.
7. Crear una OU con nombre Lab. Dentro de esta OU, crear cuatro OUs: Usuarios, Computadoras, Servidores y Grupos.
8. Crear 150 usuarios mediante Powershell y unirlos a la OU Usuarios.
9. Crear 1 grupo y moverlo lo a la OU Grupos. El grupo sólo tendrá como miembros usuarios del dominio. ¿Qué tipo de grupo se debe crear? Unir 5 usuarios a este grupo.
10. Crear GPO para que este grupo se agregué al grupo local "administrators" de todos los servidores. (Vincular GPO a la OU Servidores).
11. Crear VM Windows Server 2019 Core, implementar una CA Root Enterprise SHA2 y moverla  a la OU correspondiente.
    * Pregunta: ¿Es recomendable mover de OU los controladores de dominio?
    * Realizar configuración de AutoEnrollment para usuarios y equipos con template generico.
12. Implementar LDAPS en ambos controladores de dominio.
13. Crear VM e instalar Veeam Backup & Replication. Crear job para los dos DC. Configurar ApplicationAware.
    * Realizar restore de objetos granular de Active Directory.
14. Crear VM Windows Server 2016 Core. Crear otro forest. (Forest 2)
15. Crear relación de confianza de tipo forest entre los dos bosques previamente creados.
16. En el Forest 1 (el que se creó primero), implementar dos servidores (WS 2019 core) para File Server (DFSN y DFSR). Crear una carpeta compartida y verificar alta disponibilidad.
17. Nueva VM en Forest 1, implementar WSUS. El servidor debe ser la fuente de actualización de todos los servidores del laboratorio. Tener en cuenta que servidores productivos no deben actualizarse de manera automatica. Usar disco diferenciado para updates.
18. Actualizar todos los servidores mediante WSUS de ambos forests. 
19. Instalar dos servidores más en el Forest 1. Implementar cluster MSSQL HA (Always On). Realizar failover manual. Replicación debe ser sincrona. Revisar mejor práctica de volumes de Windows para la BD, logs, etc.
20. Para liberar recursos, eliminar las dos VM de File Servers.
21. Crear dos VM adicionales en el Forest 1. Configurar rol DHCP en alta disponibilidad. Crear un scope con una subnet ficticia (Azure no soporta VM con IP Dinamicas desde un servidor Windows).
22. Realizar backup de rol DHCP. Buscar logs.
23. Para liberar recursos, eliminar las dos VM DHCP. ¿Luego de eliminarlas, se debe hacer una modificación en Active Directory
24. Implementar dos VM  en el Forest 1. En ambas instalar IIS.
    * Una VM cumplirá el rol de Reverse Proxy. Implementarlo, debe redireccionar tráfico a la segunda VM IIS.
    * La segunda VM Web Server brindará una página estatica. Hacer modificaciones en el HTML.
    * Implementar HTTPS mediante certificado público. (Se puede usar Let's encrypt).
25. Implementar LAPS. Se debe instalar de manera automatica en todos los Members Servers y Computadoras del Forest.
