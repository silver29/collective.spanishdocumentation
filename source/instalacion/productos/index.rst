.. -*- coding: utf-8 -*-

====================================================
Agregando módulos y complementos adicionales a Plone
====================================================

.. sidebar:: Sobre este artículo

    :Autor(es): Leonardo J. Caballero G.
    :Correo(s): leonardocaballero@gmail.com
    :Compatible con: Plone 4
    :Fecha: 29 de septiembre de 2014

En esta articulo busca explicar la instalación de módulos y complementos 
adicionales a Plone 3 y Plone 4, además de no ser una guía paso a paso 
simplemente es una referencias sobre las diversas formas de hacer esto.

Introducción
============

Una de las principales características de un Sistema de Gestión de Contenido 
es la modularización. Es decir, la posibilidad de agregación nueva funcionalidad 
mediante la instalación de módulos construidos por comunidad de programadores 
que apoyan estas herramientas libre. 

Plone tiene un gran número de módulos para ampliar aún más sus funcionalidades, 
éstos se llaman productos.

Con el objetivo de satisfacer las principales demandas de tus usuarios debe aprender 
a instalar, configurar productos para que estén disponibles para habilitados en sus 
diversos sitios Plone que hospede en esa instalación.

.. warning:: 
    sin embargo, son productos de terceros, la fundación Plone no se responsable de 
    los productos de terceros.

Productos Adicionales
=====================

Para la mayor comprensión de este manual cada vez que nos refiramos a un
producto estaremos hablando de plugins para los que usen WordPress o módulos
para los que usen Joomla o Drupal, también debemos tomar en cuenta que los
temas o pieles en Plone los tratamos como un producto. dicho esto bienvenidos
a la magia de personalizar su sitio Plone.

Usted probablemente quiere agregar productos en su sitio Plone, como un
apariencia visual o temas distinto a la predeterminada, o agregar un foro de
discusión, integrar con otros servicios como *Bases de Datos*, *LDAP*, *Lista
de correo*, entre otros.

.. tip::
    Para ver la lista de productos disponibles y usted debe ser el usuario 
    **Administrador del sitio Web** y haber iniciado sesión de usuario. 

Después de, vaya a la `Configuración del Sitio`_, en Plone 4 acceda 
al menú *Personal en la esquina superior derecha con el nombre real o 
el nombre de usuario* y luego hace clic en :menuselection:`Configuración del sitio`.

.. figure:: productos_complementos_1.png
  :align: center
  :width: 640px
  :height: 448px
  :alt: Configuración del sitio

  **Configuración del sitio**

En el panel **Configuración del sitio**, haga clic en la sección **Complementos**.

.. figure:: productos_complementos_2.png
  :align: center
  :width: 640px
  :height: 388px
  :alt: sección Complementos

  **sección Complementos**

Estando en la ruta :menuselection:`Configuración del sitio --> Complementos`, le 
aparecerá la siguiente pantalla:

.. figure:: productos_complementos_3.png
  :align: center
  :width: 640px
  :height: 333px
  :alt: Complementos disponibles a Activar

  **Complementos disponibles a Activar**

Desde allí no se puede agregar productos más allá de los que se enumeran en la página.


En la sección **Complementos disponibles**, seleccione las casillas de los productos deseados 
y luego haga clic en el botón **Activar**, que se encuentra al final de los productos disponibles.

Los **productos instalados** se enumeran en la sección ubicada al final de página.
De forma predeterminada, todos los sitios cuentan con algunos productos ya instalados, 
como se muestra a continuación:

.. figure:: productos_complementos_4.png
  :align: center
  :width: 640px
  :height: 434px
  :alt: Complementos disponibles a Desactivar

  **Complementos disponibles a Desactivar**

Para remover el producto, seleccione la casillas a la lado de los productos que desea 
eliminar en la sección **Complementos activos**, y luego haga clic en el botón **Desactivar**.

.. tip::
    Si necesita instalar la integración con LDAP por favor, **no instale** el producto 
    ``LDAP User Folder``. Este producto es estándar para Plone, pero su instalación produce 
    errores que impiden el acceso a la área administrativa del sitio.

----

¿Cómo agrego productos específicos al sitio Plone?
==================================================

Hay que entender varios conceptos antes de continuar tales como: 

- :term:`Paquete Python`.

- :term:`Productos`.

- :term:`Producto Zope`.

- :term:`Producto Plone`.

- :term:`paquetes Egg`.

- :term:`Collective`.

Tipos de productos
==================

Teniendo en cuenta los conceptos previos, entonces existen muchos Productos
distribuidos disponibles como :term:`Producto Zope` o :term:`paquetes Egg`, 
pero ahora hay que saber que tipo de producto están disponibles para instalar 
y ampliar las funcionalidades de Zope/Plone, a continuación se describe una 
lista de estos:

- :term:`Temas / Apariencias`.

- :term:`Tipos de contenidos`.


Recomendaciones para agregar productos
--------------------------------------

Al momento de buscar que producto a instalar, proceda de la siguiente forma:

-   Consulte la sección llamada `Add-on Product Releases`_ del sitio Plone.org, 
    donde podrá conseguir información de los productos adicionales realizados 
    por terceros o miembros de la comunidad, muchos de los productos disponibles 
    en esta sección son productos :ref:`"al viejo estilo" <agregar_producto_zope2>`. 

    .. note:: 
        Hasta **Diciembre de 2013** hay más de **2188 proyectos** de productos 
        de terceros con **8030 publicaciones** disponibles en el sitio Web de Plone.

-   Si quiere gestionar con su buildout la instalación de los :term:`paquetes Egg`
    puede usar como referencia el sitio Python Package Index (:term:`PyPI`)
    seleccionar los nombres de :term:`paquetes Egg` y agregarlo en la sección
    ``eggs`` y ``zcml`` respectivamente.

-   Si no esta disponible ni `Add-on Product Releases`_ del sitio Plone.org ni en 
    el sitio Python Package Index (:term:`PyPI`), consulte los repositorios de código 
    fuente :term:`Collective` y gestionar la descarga del código fuente manualmente 
    o automáticamente.

Funcionamiento
==============
La herramienta ``zc.buildout`` funciona en base a los siguientes pasos ilustrados e 
descritos a continuación:

.. figure:: ./como_instalar_addons_plone.png
  :align: center
  :width: 640px
  :height: 453px
  :alt: Como instalar Add ons en Plone

  **Como instalar Add ons en Plone**

#. Las configuraciones se efectúan en el archivo :ref:`buildout.cfg <buildout_cfg>`.

#. Luego de editar sus configuraciones ejecute el comando :command:`bin/buildout`.

#. Entonces ``zc.buildout`` consulta dentro :term:`Python Package Index` 
   para comprobar la existencia del paquetes a descargar.

#. Descarga los :term:`paquetes Egg` (archivos .egg / .tar.gz) y sus dependencias que 
   estén publicados en :term:`PyPI`.

#. Finalmente se encarga de instalar como producto / paquete disponible para ser 
   habilitar / deshabilitar en su :term:`Instancia de Zope` en cualquier de sus sitios Plone.

Ejemplo de uso
==============

Para ejemplificar estos conceptos previos, agregue el siguiente producto:

.. figure:: ./screenshot_007.png
  :align: center
  :alt: El producto heddex.tranquility-theme

  **El producto heddex.tranquility-theme**

`heddex.tranquility theme`_, es un tema se empaqueta como un paquete egg Python 
y en la `página del producto en plone.org`_ tiene buenas instrucciones de instalación. 
Esta documentación dice añadir el nombre de producto ``heddex.tranquility``
debajo de la directivas ``eggs`` y ``zcml`` en parte ``[buildout]``.

Antes de seguir seria bueno que entiendas que es buildout y sus hiervas, para
esto recomiendo leer el manual sobre `Gestión de proyectos con Buildout`_.

Para empezar, es una buena idea hacer una copia de seguridad del archivo
original :file:`buildout.cfg`, sólo en caso de que accidentalmente dañe la
configuración respectivamente.

1.  Abra el archivo :file:`buildout.cfg` en su editor de texto de elección.

2.  Buscar la sección etiquetada: ``[buildout]``.

3.  Buscar la linea que tenga la directiva: ``eggs =``.

4.  Agregar ``heddex.tranquility`` por debajo de la lista de :term:`paquetes Egg`,
    dejando cuatro espacios en blanco antes del nombre del paquete.

5.  Buscar la linea que tenga la directiva: ``zcml =``.

6.  Agregar ``heddex.tranquility`` por debajo de esa línea, dejando
    cuatro espacios en blanco antes del nombre del paquete.

7.  Guarde su archivo de configuración :file:`buildout.cfg`.

8.  Ejecute el script buildout, de la siguiente forma: :command:`./bin/buildout -vN`.

9.  Inicie de nuevo Plone, de la siguiente forma: :command:`./bin/instance fg`.

10. Abra el navegador web de su preferencia, acceda a su dirección del
    sitio Plone, por defecto es `Productos Adicionales`_ y justo al lado
    del producto ``heddex.tranquility`` y luego haga clic en el botón
    **Instalar** . Hasta este punto solo debe aparecer en la lista de los
    **Productos instalados**, si hasta este punto no ha cambiado la
    apariencia del sitio de Plone debe ir a la sección `Configuración de Temas`_
    y cambiar el **Tema predeterminado** por el de su gusto.

.. note::

  Es necesario respetar los 4 espacios de izquierda a derecha como se
  describen a continuación:

.. code-block:: cfg

  eggs =
      heddex.tranquility
  ...
  zcml =
      heddex.tranquility

.. _agregar_producto_zope2:

Agregando un producto tradicional Zope 2
----------------------------------------

La forma más sencilla de probar un producto tradicional de Zope 2 es para
extraerlo en dentro de la carpeta :file:`products/` de instalación. Si ves
documentación referente a la carpeta :file:`products/` en una instancia de Zope, esta
es la misma cosa.

Sin embargo, este enfoque hace que sea más difícil para redistribuir su
proyecto y compartirlo con otros programadores. A menudo es más predecible
dejar que buildout descargue e instale el paquete por usted. Puede hacer esto
con la sección ``[productdistros]`` del archivo :file:`buildout.cfg`.

.. code-block:: cfg

  ...

  [productdistros]
  recipe = plone.recipe.distros
  urls =
      http://plone.org/products/docfindertab/releases/1.0.4/Products.DocFinderTab-1.0.4.zip
      http://plone.org/products/windowz/releases/1.2/windowZ-1.2.tgz
  nested-packages =
  version-suffix-packages =

  ...

Este método también es conocido como **"al viejo estilo de Zope"**  y la
razón de este mecanismo es por que algunos productos no están aun empaquetado
como :term:`paquetes Egg` de Python. Estos productos necesitan ser instalados usando
sus enlaces de descargas como se demostrado previamente. Su usted busca un
producto que usted quiere usar que no este empaquetado como :term:`Egg`, usted
necesita buscar el enlace de descargas en la página de productos en plone.org
y coloque la dirección URL.

.. _agregar_producto_desarrollo:

Agregando un paquete "desarrollo"
---------------------------------

A veces usted tiene que existen algunos productos que no están empaquetados en :term:`Egg` 
ni **al viejo estilo de Zope**, pero estos están disponibles desde un repositorio de control 
de versiones como SVN, Git, o simplemente son varios productos locales en desarrollo. 

Usted puede hacer dos cosas para instalar entonces. Lo primero que hay que hacer es 
construirlo y colocarlo al directorio :file:`src/` de su instalación Plone. Esto también 
es muy útil cuando usted modifica un producto existente. Antes de ejecutar el comando
:command:`buildout` usted tiene que agregar los productos a las secciones ``eggs`` y
``zcml`` (si es necesario) de archivo :file:`buildout.cfg`:

.. code-block:: cfg

  ...
  eggs  =
      ...
      canaima.aponwaotheme
      ...
  zcml =
      ...
      canaima.aponwaotheme
      ...
  develop =
      ...
      src/canaima.aponwaotheme
      ...

Luego ejecuta el siguiente comando dentro del directorio :file:`src/`:

.. code-block:: sh

  $ git clone git://gitorious.org/~macagua/canaima-aponwao-plone-theme/canaima-aponwaotheme.git canaima.aponwaotheme


.. tip:: 
    debe realizar un comando :command:`svn checkout` al directorio :file:`trunk/` 
    o al directorio :file:`tags/` del producto de la versión estable que necesita 
    utilizar dentro del directorio :file:`src/` y luego configurarlo como se describe 
    previamente en la sección llamada **Agregando un paquete "desarrollo"**.

Luego reconstruye el el sitio con el siguiente comando: 

.. code-block:: sh

  $ ./bin/buildout -vN

Este es un tema para Plone 3 y Plone 4 que aun esta en desarrollo:

.. image:: ./canaina-website.png
  :alt: Canaima Aponwao Theme
  :align: center

El paquete `canaima.aponwaotheme`_, es un tema para sitios Plone 3.

.. note::

  Cabe destacar que ya existente `extensiones de Buildout`_ que gestión
  descargas desde repositorios de control de versiones como
  `mr.developer`_ y `infrae.subversion`_ que con unas simples
  configuraciones adicionales en tu archivo :file:`buildout.cfg` puede automatizar
  la descarga de los códigos fuentes del los respectivos repositorios.


Algunos productos adicionales útiles
------------------------------------

Una serie de productos útiles que sirven de ejemplo para poner en practica
las configuraciones en su archivo :file:`buildout.cfg`

.. note:: 

  Los tres puntos suspensivos ``...`` son la indicar que tienes una serie
  de configuraciones antes o después de la sección, así que **NO** se copian ;)


Editor de texto enriquecido
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Existe varios editores de texto enriquecido como `TinyMCE`_ y
`Products.FCKeditor`_, adicionalmente al editor por defecto que ofrece Plone
como es Kupu.

Editor de texto enriquecido

.. image:: ./screenshot.jpeg
  :align: center
  :alt: TinyMCE

----

.. image:: ./screenshot_004.jpeg
  :align: center
  :alt: Products.FCKeditor

Agregue la siguiente configuración del producto al archivo :file:`buildout.cfg`

.. code-block:: cfg

  eggs =
      ...
      Products.FCKeditor
      Products.TinyMCE


Foros de discusión
~~~~~~~~~~~~~~~~~~

`Ploneboard`_, es uno de los más usados en la mayoría de sitios Plone. Si
usted necesita realmente un foro avanzado usted más bien debe buscar fuera
del sitio de Plone y tratarte de integrarlo a su sitio.

.. image:: ./ploneboard04.png
  :align: center
  :alt: Foro de discusión con el producto Ploneboard

Agregue la siguiente configuración del producto al archivo :file:`buildout.cfg`

.. code-block:: cfg

  eggs =
      ...
      Products.Ploneboard

Calificaciones
~~~~~~~~~~~~~~

`plone.contentratings`_, es un producto que permite definir categorías de
calificaciones, tipo de calificación y aplicarla a los diversos tipos  de
contenidos de tu sitio Plone. Un ejemplo del uso este `sitio`_ que usa este
producto en la sección **Editor's rating** la cual posee 4 categorías y el
tipo de calificación esta basado por Estrellas.

.. code-block:: cfg

  eggs =
      ...
      plone.contentratings
      ...
  zcml =
      ...
      plone.contentratings


Bitácoras
~~~~~~~~~

Yo he probado los productos `Quills`_ y `Scrawl`_, el primero es muy parecido
a las características que ofrece Wordpress y el segundo es muy minimalista.


.. image:: ./screenshot_005.png
  :align: center
  :alt: Bitácoras/Blogs con el producto Quills

----

.. image:: ./screenshot_004.png
  :align: center
  :alt: Bitácoras/Blogs con el producto Scrawl

Agregue la siguiente configuración del producto al archivo :file:`buildout.cfg`

.. code-block:: cfg

  eggs =
      ...
      Products.Quills
      Products.Scrawl


Sistema de noticias
~~~~~~~~~~~~~~~~~~~

Altamente recomendada es el producto `Singing and Dancing`_.

.. image:: ./screenshot_003.png
  :align: center
  :alt: Sistema de correo de noticias con el producto Singing and Dancing

Agregue la siguiente configuración del producto al archivo :file:`buildout.cfg`

.. code-block:: cfg

  extends =
      ...
      https://svn.plone.org/svn/collective/collective.dancing/buildout-extends/0.9.0.cfg
      ...
  [instance]
   ...
   eggs =
       ...
       collective.dancing
       ...
   zcml =
       ...
        collective.dancing
       ...

Etiquetas
~~~~~~~~~

`quintagroup.portlet.cumulus`_, es un portlet de nubes de etiquetas que rotan usando una animación de Flash 3D.

.. image:: ./screenshot_002.jpeg
  :align: center
  :alt: Nube de etiquetas con el producto quintagroup.portlet.cumulus

Agregue la siguiente configuración del producto al archivo :file:`buildout.cfg`

.. code-block:: cfg

  eggs =
      ...
      quintagroup.portlet.cumulus
      ...
  zcml =
      ...
      quintagroup.portlet.cumulus
      ...

Media
~~~~~

`ATGoogleVideo`_, agrega un tipo de contenido que hace referencias a vídeos
almacenados en Google Video o YouTube dentro de un sitio Plone

.. image:: ./screenshot.png
  :align: center
  :alt: ATGoogleVideo

Agregue la siguiente configuración del producto al archivo :file:`buildout.cfg`

.. code-block:: cfg

  eggs =
      ...
      Products.ATGoogleVideo

`Gallery portlet`_, un portlet para presentar galerías fotográficas.

.. image:: ./screenshot_002.png
  :align: center
  :alt: portlet de Galería de imágenes Gallery portlet

Agregue la siguiente configuración del producto al archivo :file:`buildout.cfg`

.. code-block:: cfg

  eggs =
      ...
      se.portlet.gallery
  zcml =
      ...
      se.portlet.gallery

`plone.app.imaging`_, le habilita declarativamente definir adicionales tamaños
de imágenes inicialmente generadas cuando usted agrega imágenes en su portal.

.. image:: ./screenshot_006.png
  :align: center
  :alt: plone.app.imaging

Agregue la siguiente configuración del producto al archivo :file:`buildout.cfg`

.. code-block:: cfg

  eggs =
      ...
      plone.app.imaging
      ...
  zcml =
      ...
      plone.app.imaging
      ...

Seguridad
~~~~~~~~~

`Plone Captchas`_, agrega mecanismos de captcha para si sitio Plone.

.. code-block:: cfg

  eggs =
      ...
      quintagroup.plonecaptchas
      ...
  zcml =
      ...
      quintagroup.plonecaptchas
      ...

Administración
~~~~~~~~~~~~~~

`Anonymous view`_, es bastante útil porque le permite a usted mostrar ciertas
páginas que estarán disponibles a usuarios anónimos.

.. code-block:: cfg

  eggs =
      ...
      collective.anonymousview
      ...
  zcml =
      ...
      collective.anonymousview
      ...

`collective.uploadify`_, si usted le gustaría subir varios archivos de una
ves usted tiene que instalarlo.

.. image:: ./screenshot_003.jpeg
  :align: center
  :alt: collective.uploadify

Agregue la siguiente configuración del producto al archivo :file:`buildout.cfg`

.. code-block:: cfg

  eggs =
      ...
      collective.uploadify


Referencias
===========

- `Installing Plone add-ons - quick instructions`_.

- `Using Add-ons`_.

- `Add on product installation fails`_.

- `Installing a third party product`_.

- `Packages, products and eggs`_.

.. _Third-Party Products: http://plone.org/documentation/kb/add-ons/tutorial-all-pages
.. _Products.CMFPlone: http://pypi.python.org/pypi/Products.CMFPlone
.. _sitio web de PEAK: http://peak.telecommunity.com/DevCenter/setuptools
.. _obtener acceso de escritura al repositorio: http://plone.org/countries/conosur/documentacion/obtener-acceso-de-escritura-al-repositorio-svn-de-plone
.. _crear su estructura básica de repositorio: http://plone.org/countries/conosur/documentacion/crear-un-nuevo-proyecto-en-el-repositorio-collective-de-plone
.. _enlace: http://svn.plone.org/svn/collective/
.. _Configuración de Temas: http://localhost:8080/Plone/@@skins-controlpanel
.. _Configuración de Productos Adicionales: http://localhost:8080/Plone/prefs_install_products_form
.. _su instalación: http://localhost:8080/manage
.. _Add-on Product Releases: http://plone.org/products
.. _heddex.tranquility theme: http://plone.org/products/heddex.tranquility-theme
.. _página del producto en plone.org: http://plone.org/products/heddex.tranquility-theme
.. _Gestión de proyectos con Buildout: http://coactivate.org/projects/ploneve/gestion-de-proyectos-con-buildout
.. _Productos Adicionales: http://localhost:8080/Plone/prefs_install_products_form
.. _canaima.aponwaotheme: http://gitorious.org/%7Emacagua/canaima-aponwao-plone-theme/canaima-aponwaotheme
.. _extensiones de Buildout: http://pypi.python.org/pypi?:action=search&term=Buildout&submit=search
.. _infrae.subversion: http://pypi.python.org/pypi/infrae.subversion
.. _mr.developer: http://pypi.python.org/pypi/mr.developer
.. _TinyMCE: http://plone.org/products/tinymce/
.. _Products.FCKeditor: http://plone.org/products/fckeditor
.. _Ploneboard: http://plone.org/products/ploneboard
.. _plone.contentratings: http://plone.org/products/plone-contentratings/
.. _sitio : http://www.contentmanagementsoftware.info/plone/plone-contentratings
.. _Quills: http://plone.org/products/quills/
.. _Scrawl: http://plone.org/products/scrawl/
.. _Singing and Dancing: http://plone.org/products/dancing/
.. _quintagroup.portlet.cumulus: http://plone.org/products/quintagroup.portlet.cumulus
.. _ATGoogleVideo: http://plone.org/products/atgooglevideo/
.. _Gallery portlet: http://plone.org/products/gallery-portlet/
.. _plone.app.imaging: http://plone.org/products/plone.app.imaging/
.. _Plone Captchas: http://plone.org/products/plone-captchas/
.. _Anonymous view: http://plone.org/products/collective.anonymousview/
.. _collective.uploadify: http://plone.org/products/collective.uploadify/
.. _Installing Plone add-ons - quick instructions: http://plone.org/documentation/kb/installing-add-ons-quick-how-to
.. _Using Add-ons: http://plone.org/documentation/kb/add-ons/tutorial-all-pages
.. _Add on product installation fails: http://plone.org/documentation/kb/diagnosing-third-party-product-installation-problems
.. _Installing a third party product: http://plone.org/documentation/manual/developer-manual/managing-projects-with-buildout/installing-a-third-party-product
.. _Packages, products and eggs: http://plone.org/documentation/manual/developer-manual/managing-projects-with-buildout/packages-products-and-eggs/
.. _Configuración del Sitio: http://www.ufrgs.br/tutorial-plone4/dicas-iniciais/configuracao-do-site
