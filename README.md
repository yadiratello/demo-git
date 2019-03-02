# 			GIT

1. Mostrar la version de git instalado
```console
  git --version
```

2. Como autenticarme en la terminal.
```  
  git config --global user.name "nombreUserGitHub"
  
  git config --global user.email "email@gmail.com"
```

3. Como verificar de quien es la maquina(quien esta logueado en esta terminal) obtiene las credenciales(name,email)
```  
  git config --global -l
  
  git config user.name
  
  git config user.email
  
```

4. Indicarle a GIT que carpeta sera mi repositorio(proyecto=repositorio)
```  
  git init
```
* se creare una carpeta oculta .git
* borrar la carpeta en caso ya no quiera seguir los cambios de esa carpeta


5. Como saber cual es el estado(status) actual de mis archivos 
```  
  git status
```
* rojo: no esta siendo controlado
* verde: si esta siendo controlado


6. Decirle a git que siga los cambios de todo mi repositorio(que tenga el control de todo) 
```  
  git add . 
```  
* . sigue los cambios de todo mi directorio actual

* al hacer git add . mis archivos pasan a una zona llamada stage

* stage: es una zona intermediaria en donde estan nuestros archivos listos para ser confirmados.


7. Como confirmo los cambios 
* Aqui ya deja la zona del stage
```  
  git commit -m "Comit Inicial"
```
* -m es para indicar un mensaje descriptivo


8. Como verificar cual fue la ultima modificacion q se ha hecho de lo q teniamos confirmado
```  
  git diff
```

9. Como revertir la situacion(ctr+z) a una situacion anterio(mi ultimo commit)
```  
  git checkout
```

10. ver la lista de cambios(commit) que hemos realizado
```
git log
```
* muestra desde el commit mas actual hasta el mas antiguo


11. modificar el contenido de un unico archivo en particular
```  
  git add nombreArchivo.html
  
  git commit -m "mensaje commit"
```

12. Agregar a la zona del stage un directorio en particular
```  
  git add nombreDirectorio/
```

13. Agregar a la zona del stage todo el contenido del directorio css cuyos archivos terminen en la extension .css
```  
  git add css/*.css
```

14. Si quisiera quitar de la parte stage un archivo en particular o un conjunto de archivos :
```  
  git reset nombreArchivo
  
  git reset nombreCarpeta/
```

15. Otra forma de agregar todos los archivos a la parte del stage
```  
  git add -A
  
  git add --all
```

16. Como colocar ALIAS a los comandos de GIT
```  
  git config --global alias.nombreAlias "comandoAReemplazar"
```
ejm:
```  
  git config --global alias.s "status"
```

17. Como modificar el mensaje de mi commit
Ejm:
```  
  git commit -m "Nueva modificion al ndex" <-- modificar esto
```
```  
  git commit --amend -m "Nueva modificacion al index"
```  

18. Como reenombrar los archivos que ya fueron commiteados en GIT
* comando mv(modifica el nombre de mi archivo)
```  
  git mv principal.html princ.html
  
  git commit -m "Se cambio de nombre al archivo principal.html a princ"
```

19. ComoRemover o eliminar un archivo en especifico
* comando rm(remove)
```  
  git rm princ.html
  
  git commit -m "Se Elimino el archivo principal.html"
```

20. Como borrar un cambio en GIT
* reset --soft: vuelve un paso atras de nuestro cambio. Cuando colocas --soft no esta recuperando los elementos. Solo se esta ubicando en ese lugar
```  
  git reset --soft idDelCambioAlCualQuieroRegresar
``` 


21. Si queremos q los archivos se recuperen(usar --hard)
```  
  git reset --hard 00082e1152e3021a593e959871422b0a6833b29
```
* 300082e1152e3021a593e959871422b0a6833b29(id del archivo a recuperar) se obtiene con git log


###                        	GITIGNORE     

- sirve para excluir ciertos archivos de nuestro proyecto q son innecesarios(ejm: archivos de configuracion(ide-config)).
- Para exluirlos solo debemos de crear un archivo con la extension .gitignore y debe de estar al mismo nivel de la carpeta .git
- Abrimos este archivo y simplemente guardamos el nombre del archivo que queremos excluir.
- Escribir los siguientes comandos en la terminal de GIT
```
touch .gitignore 

cat .gitignore

ide-config
```
* Estamos ignorando de nuestro proyecto los cambios que se realizen al archivo ide-config


22. Como decirle a GIT que no lleve el control de mis archivos q estan en la carpeta config y mis archivos .class
* Debemos de colocar en el archivo .gitignore lo siguiente: 
```
cat .gitignore

/config/ 

.class
```

###                             RAMAS Y UNIONES 
                             
- Una rama viene a ser una division de tu trabajo actual con el objetivo de poder realizar en esa nueva division quizas algunos cambios q tal vez no estes seguro q formen parte de la rama principal.

- 1er tipo de MERGE:
- Fast-Forward: Este tipo de merge al detetcar que no hay nigun cambio sobre nuestra rama principal de forma transparente puede hacer la union de nuestra rama secundaria con la rama inicial
- Si quisieramos iniciar unanueva funcionalidad a nuestro sistema(una nueva pag) por ejm: nuevaFuncionalidad.html
 
23. Para crear una nueva rama q viene a ser una bifurcacion de la rama principal, escribios lo sgte:
```
  git branch nombreRama
```


- lista de una manera mas resumida las ramas en la que me encuentro(el HEAD apunta -> a la rama en q se encuentra) o tmb en la ruta se ve la rama actual esta () ejm: lctuser@lctuster MINGW64 /d/CURSO_GIT/sitio_web1 (master)
- Por defecto me encuentro en la rama master

24. Ver mas detallado mis commits y mis ramas
```  
  git log --oneline --decorate --all --graph
```


25. Como cambiar de rama?
```  
  git checkout nombreRama
```
ejm:
lctuser@lctuster MINGW64 /d/CURSO_GIT/sitio_web1 (rama_funcionalidad)
```  
  git add .
  
  git commit -m "Primer commit de esta rama"
```
- Al hacer el commit en la rama_funcionalidad esos archivos ahora le pertenecen a la rama en la q se hizo el commit


26. Si quiero regresar a la rama anterior q es(master)
```  
  git checkout master
```

- Como trabajar en la union de la rama principal con la rama secundaria
- queremos integrar la rama_funcionalidad con la rama principal(master)
- 1. primero nos dirijimos a la rama principal 
```  
  git checkout master
```
- 2. Aqui hacemos un git merge con el nombre de la rama q queremos unir
```  
  git merge rama_funcionalidad
```
- De esta manera ya estan unidad ambas ramas, la rama master con la rama sencundaria. Por lo tanto la rama_funcionalidad ya no es necesaria tenerla y la podemos eliminar. 
```  
  git branch -d rama_funcionalidad
```
- Ahora solo tenemos la rama master con el commit de la rama_funcionalidad
```  
  git log --oneline --decorate --all --graph
```


- Si quisieramos crear una nueva rama pero que apenas la cree me rediriga(cambie) a ella
```
  git checkout -b rama_opcion
```  
- -b = branch
* el prompt se parecera a esto:
* lctuser@lctuster MINGW64 /d/CURSO_GIT/sitio_web1 (rama_opcion)
```
  git merge rama_opcion

  git branch -d rama_opcion
```


### MERGE con Conflictos 
```
  git merge nueva_rama
```
- saldra este mensaje:
- Auto-merging nuevaOpcion.html
- CONFLICT (content): Merge conflict in nuevaOpcion.html
- Automatic merge failed; fix conflicts and then commit the result.

- Abrimos el archivo nuevaOpcion.html y quitamos las lineas que se han generado con simbolos >>>


##              ETIQUETAS (Tags)

* Nos van a permitir a nosotros los programadores llevar un mayor control de que es lo que estamos haciendo y poder versionar y poder hacer un versionamiento mas ideal y saber que paso hasta ese punto del commit.*
* Una etiqueta es como nombrar a un commit que tenemos a lo largo de nuestras ramas(ejm:version1, version1.1, alpha, beta, etc). *

- Como Crear una etiqueta en GIT?
```  
  git tag nombre_etiqueta
```

- Como Ver las etiquetas creadas?
```  
  git tag
```

- al hacer un git log --oneline --decorate --all --graph vemos q nuestra rama presenta el  nombre de mi etiqueta creada. Al momento q estemos trabajando en un proyecto va a haber una etapa en la q queramos hacer un hito en donde indique q es la version 1.0 y sobre eso empezamos a hacer otros desarrollos y cuando ya estes seguro de una version nueva puedes etiquetarla como la version 2 


- Si quisieramos eliminar esa etiqueta
```  
  git  tag -d nombre_etiqueta
```

- A veces es mejor indicar un mensaje adicional que represente que se hizo en esa etiqueta 
```  
  git tag -a v1.1.0 -m "version 2"
```
- En el tema de versionamiento el "v" significa version, el numero inicial significa el tipo de version mayor, el segundo numero significa un cambio moderado, el tercero significa un cambio mas pequeño y minimo. 

ejm:

v2.0.0 <- ha habido un cambio importante y grande
v1.1.0 <- ha habido un cambio moderado 
v1.0.1 <- ha habido un cambio pequeño inperseptible para el usuario 
```
  git tag -a v1.0.0 -m "version inicial"
```
* -m es para agregar un mensaje descriptivo


- Como mostrar todo el detalle que hay hasta ese commit
```  
  git show v1.0.0
```

- que pasaria si tuviesemos un commit con anterioridad y ese commit para mi represento una version previa que tmb hubiese querido etiquetarla
- Se podria hacer lo siguiente:
```  
  git log --oneline --decorate --all --graph 
```
- con el codigo de arriba obtengo todos mis commits y veo en donde quiero etiquetar como otro cambio importante para mi y quiero ponerle una etiqueta. Copio el identificador de ese commit (ejm:99f53fc) y escribo lo siguiente en la terminal:
```  
  git tag -a v0.0.1 99f53fc -m "version beta"
```
- el 99f53fc es un idntificador de uno de mis commits al cual quiero etiquetar.

- Hacemos un git log --oneline --decorate --all --graph para ver si se ha etiquetado correctamente a mi commit. Y si esta todo bien tiene que aparecer el nombre de mi etiqueta al costado de mi identificador de commit.
- Algo como esto tendria que mostrarse en la terminal
- 99f53fc (tag: v0.0.1) Se creo el archivo .gitignore y se agrego dentro el archivo ide-conf


-  Tambien se puede crear una etiqueta que tenga un nombre en texto y no en numeros. Ejm:
```  
  git tag -a alpha_0.1 15aaa33 -m "version alpha"
```

- Pero que pasa si me equivoque en el etiquetado ejm: si hubiese querido etiquetar a otro commit. Solo debo de borrar la etiqueta y listo  
```  
  git tag -d alpha_1.0
```

###            GITHUB (git clone) 

1. Crear una cuenta en GitHub y loguearse. 
- GitHub es una plataforma en el cual vamos a poder subir gracias a GIT nuestros repositorios y de esta manera poder compartir nuestros proyectos.
  

2. Crear un repositorio en GitHub llamado demo-repo.
New Repository > demo-repo  > Create Repository

- Al  momento de crear un repositorio en GitHub nos saldra una pantalla indicando una ista de comandos que debemos de escribir en nuestra terminal.
 

3. Creo un proyecto llamado folder2, despues dentro de folder2 creo un archivo prueba.html
- Inicializo un repositorio de Git
```  
  git init
  
cat > prueba.html
HolaMundo
```
- Agrego a la zona de stage prueba.html
```  
  git add prueba.html
  
  git commit  -m "Primer commit"
```

- Como enlazar mi repositorio que he creado en GitHub a mi repositorio en local
```  
  git remote add origin https://github.com/yadira123/demo-repo.git
```

- Ahora ejecutamos el ultimo comando
```  
  git push -u origin master
```
- Me pedirá el usuario y clave de mi cuenta en GitHub
Username for 'https://github.com': yadira123

- Saldra una ventanita pidiendome mi contraseña de gitHub
- Escribo mi password y saldra los cambios y mis commit en mi repositorio en GitHub. Listo ya estan conectados ambos repositorios 



- Creare otro repositorio en GitHub para almacenar mi repositorio sitio_web1 al cual hemos trabajado durante todo este curso.
New > demo-repo2 > Create

- Hacemos el remote ya q ya no hay commits q hacer
```  
  git remote add origin https://github.com/yadira123/demo_repo2.git
```
- Hacemos el push
```  
  git push -u origin master
```


- Que pasaria si tuviese que trabajar en otra maquina distinta  y quisiera tener mi trabajo q he estado realizando
- tendria que clonar mi repositorio, creo una carpeta(ejm: folder3):
```
cd ..
mkdir folder3
cd folder3
```
- Hago Click en el boton Clone or Download de mi repositorio que quiero clonar y saldra una ruta, copio esa ruta, y en la terminal de git escribo lo sgte:
```  
  git clone https://github.com/yadira123/demo_repo2.git
```
- y se empezara a copiar todo mi repositorio demo_repo2  a folder3. Entramos a esta carpeta demo_repo2 y modificaremos el archivo princ.html
```
cd demo_repo2
cat > princ.html
<p>Hola Mundo</p>
```
```  
  git add princ.html
  
  git commit  -m "se modificó princ.html"
```

- Ahora hacemos un push 
```
git push origin master
```
- Y con este codigo de arriba, estoy diciendo: quiero que mandes mis cambios a la rama de origen master q esta en GitHub... y se envia el codigo actualizado 



###           	GIT PULL	  

* Para poder descargar los ultimos cambios que haigan podido surgir en nuestro repositorio

* En GitHub, dentro de la carpeta js/ creamos un archivo llamado opcion.js 

* y le hacemos un commit desde GitHub, le colocamos un nombre y una descripcion 

* Pero si hacemos un ls a la carpeta js/  vemos que no se ha agregado opcion.js. Entonces como hacemos para poder traer esa informacion?
* Existen dos comandos: git fetch y git pull
  
  git fetch: trae los cambios y despues tendriamos que hacerle un merge
  
  git pull:  es una forma mas practica de traer los cambios y que esos cambios se unan directamente a la rama principal(master)
```  
  git pull
```
* Ahora si podemos ver al archivo opcion.js y si hacemos un git log --oneline --decorate --all --graph podemos ver el commit que hicimos en GitHub 



###                 FORK    

* En muchas ocasiones podemos ver en GitHub algunos repositorios que son de nuestro agrado en donde nosotros queremos quizas hacerle una copia y hacerles algunas modificaciones para eso GitHub nos proporciona una funcionalidad llamada "fork"

1. Para hacer un fork primero tenemos q dirigirnos al repositorio que queremos tener o hacer una copia en nuestro repositorio de GitHub.

2. Damos click en el boton "Fork" que se encuentra al costado del nombre del repositorio, y automaticamente GitHub va a poner una copia de ese repositorio en mi cuenta personal de GitHub.
 
* Si quisieramos trabajar en ese repositorio, los cambios no van a ir al repositorio original si no a nuestra copia en local.*

3. Si quisieramos traer ese repositorio que hemos hecho el fork a mi maquina(pc) en local:

3.1. Creamos una carpeta en local y dentro de el abrimos una terminal y ejecutamos el comando git clone con la ruta de ese repo que esta en GitHub ejm:
```
git clone https://github.com/yadira123/diseno-web-componentes-php-2018.git
```
3.2.  Vamos a modificar cualquier archivo
```  
  git add .
  
  git commit -m "Se modifico el archivo index.php"
  
  git push origin master
```
- Importante: Hacer el git push para que los cambios aparezcan en mi repositorio de GitHub y en local


* En ocaciones quisieramos sugerir algun cambio para que el autor original de ese repositorio lo revise y pueda agregarlos o no a ese repositorio*


###             PULL REQUEST 	
1. Primero hacemos todo el proceso del fork a cualquier repositorio de GitHub de otro usuario, en este caso hare un fork a repo demo_git

2. Creo un directorio en local e ingreso a ese directorio y hago un:
```
git clone https://github.com/persiano13/demo-git.git
```
- estoy logueada con la cuenta de Persiano13 y voy a sugerir a la cuenta yadira123 q es el autor de ese repositorio que haga algunos cambios pero antes modificare cualquier archivo( en este caso sera opcion.js)
```
cat > opcion.js
alert('Esto agrego persiano13');
```
- Ahora hago el commit y el git push
```  
  git add opcion.js
  
  git commit -m "Se agrego un alert a opcion.js"
  
  git push origin master
```

- Ahora quiero que el cambio que he hecho se vea reflejado en el repositorio original que le pertenece a otro autor 

- Para hacer pull request simplemente nos dirijimos a nuestro repositorio y hacemos click en el boton "New pull request", y va a salir una ventana resumen de cuales son los cambios que van a verse afectados con la rama original del repositorio de la cuenta principal, entonces hago click en el boton "Create pull request" y escribo un titulo por ejm: "Se agrego un alert a opcion.js" y escribo una descripcion de mis cambios y doy click en "Create pull request" y me saldra un mensaje indicando que no tendre ningun tipo de problema con la rama principal.

- Ahora el autor original del repositorio podra visualizar el cambio que hizo el usuario persiano13 y ver si agrega o no los cambios.

- Para visualizar el cambio d otros usuarios a mi repositorios: Ir a la opcion Pull requests 

- Para confirmar ese cambio que ha hecho en mi repo demo_git el usuario persiano13 solo hago click en "Confirm Merge" y saldra un mensaje parecido:

yadira123 merged commit 0e1b122 into yadira123:master  14 hours from now


###       	Integracion de GIT con Netbeans, Eclipse, etc 

1. Integracion de un proyecto en GitHub con mi ide NetBeans

1.1. Primero subo algun proyecto a mi cuenta en GitHub. En mi caso sera un proyecto en java

1.2. Cierro todos mis proyectos que tenga abierto en NetBeans por que si no, no me saldra la opcion de Git.

1.3. En la barra de Menu hago clic en la opcion:
      Team > Git > Clone

* Obviamente es el comando para poder clonar el repositorio que tenemos en la cuenta de GitHub 
* Para obtener la url del repositorio voy a GitHub y doy en Clone or Download y copio la url
* Esto implica que tmb podria utilizarlo si utilizo BitBucket, GitLab, etc.

1.4. Me saldra una ventana  pidiendome:
 Repository Url: https://github.com/yadira123/Ejercicios_Java_SE.git

1.5. Digito mis credenciales de acceso(usuario y contraseña de GitHub). ejm:
yadira123
************

1.6 Establesco la ruta en la cual se va a clonar ese repositorio (mi repositorio de GitHub)
D:\CURSOS_MITOCODE\CURSO_JAVA7_SE_BASICO\Ejercicios_Java_SE_git  

1.7. Next y saldra una ventana, escogo la rama principal, Next y Finish.

*Con esto el repositorio que tenia en GitHub voy a tener disponible en local y n mi ide 


2. Si por alguna razon hago un cambio y quiero guardar los cambios en GitHub:

2.1. Agregar los cambios que he hecho en el proyecto, desde NetBeans:
Click derecho en el proyecto de NetBeans > Git  > Add
* Lo que hemos arriba es agregar los cambios al stage 

2.2. Ahora tenemos que confirmar los cambios
Click derecho en el proyecto de NetBeans > Git > Commit

2.3. Saldra una ventana y agregamos un mensaje al commit:
Ejm:
Se comento el ejercicio 5  y doy click en el boton commit

*Pero si voy a a terminal y hago un git log, aun no  podre visualizar los cambios ni el commit realizado.

2.4. Para enviar los cambios que acabamos de hacer a nuestra cuenta de GitHub hacemos lo siguiente:
Click derecho en el proyecto > Git  > Remote > Push

Seleccionamos Select Configured Git Repository Location

* De esta forma mi proyecto se conectara con mi repositorio en GitHub, seleccionamos la rama  y Finish. 
