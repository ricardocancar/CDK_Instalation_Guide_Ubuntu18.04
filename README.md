# CDK_Instalation_Guide_Ubuntu18.04
Este repositorio tiene como proposito unicamente describir el proceso de instalación de la libreria CDK en python 3.6 para sistema Operativo Ubuntu 18.04

# Instalacion CDK MAQUINA LOCAL

## Descarga archivo binario de node js 
Instalar npm por `sudo apt-get install npm` esta 3 versiones por detras de la version de la fuente asi que se generan errores al realizar la instalancion del cdk

por lo que tenemos que ir directamente a [nodejs](https://nodejs.org/en/download/) y descargar la version 
**linux binari x64** 64 bit


```
sudo mkdir /usr/lib/node/nodejs
sudo tar -xJvf node-v10.16.0-linux-x64.tar.xz
sudo mv path/to/node-v10.16.0-linux-x64.tar.xz /usr/lib/node/nodejs
```  


### update ~/.profile
Añadir en la ultima linea.

```
nano ~/.profile
# Nodejs
export NODEJS_HOME=/usr/lib/node/nodejs
export PATH=$NODEJS_HOME/bin:$PATH
```
### Refresh profile

```
$ . ~/.profile
```

### Crear **sudo** link:

```
sudo ln -s /usr/local/lib/nodejs/node-$VERSION-$DISTRO/bin/node /usr/bin/node

sudo ln -s /usr/local/lib/nodejs/node-$VERSION-$DISTRO/bin/npm /usr/bin/npm

sudo ln -s /usr/local/lib/nodejs/node-$VERSION-$DISTRO/bin/npx /usr/bin/npx
```

por ultimo se ejecuta la instrucción

`$ sudo npm install -g aws-cdk`


## Credenciales.
Para poder modificar la infraestrucutra o replicarla en otra region mediante CDK es necesario identificarse para ello escribimos los siguientes comandos en la home:

```
$ mkdir ~/.aws
cd .aws
$ touch config
```

Luego se insertan el access key id y el secret access key id de aws.

```
[profile prueba]
aws_access_key_id=aws access key id
aws_secret_access_key=aws secret access key
region=region
```

## nuevo proyecto.

Primero se crea el directorio del nuevo proyecto y luego se inicia.

```
mkdir nuevo_proyecto
cd nuevo_proyecto
cdk init -l python
```

Esto creara una plantilla base con los scripts necesarios para crear el código de la infraestructura que se desee realizar. Además se creara un nuevo entorno .env en el cual lo aprovecharemos para instalar todas las librerias necesarias para crear nuestra infraestructura.
para ello activamos el entorno virtual:

```
$ source .env/bin/activate
```
una vez dentro del entorno virtual, instalamos la libreria aws-cdk para python aprovechando el requirements.txt que se creo al iniciar un nuevo proyecto
```
$ pip3 install -r requirements.txt
```
