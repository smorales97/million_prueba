# **Python app microservice**

Este repositorio contiene los archivos necesarios para construir y desplegar un microservicio en Python utilizando Docker y Kubernetes, a continuación esta la descripción de como hacerlo.

### **Contenido:**

**_Dockerfile:_** Archivo de configuración para construir la imagen Docker del microservicio.

**_pod_kubernetes.yml:_** Definición del Pod en Kubernetes.

**_network_kubernetes.yml:_** Política de red para controlar el tráfico dentro del clúster de Kubernetes.

**_azure_pipeline_k8s:_** Configuración del pipeline para el despliegue en Azure.

**_observabilidad Million:_** Diagrama para mejorar la observabilidad de la aplicación.

**_rendimiento_app:_** Diagrama de solución para el problema de rendimiento de la app.

### configuración

## 1. Configurar el proyecto en Azure DevOps.

 1.1 Crear un nuevo proyecto o elegir uno existente, en caso de que exista.
 
 1.2 Integrar Azure DevOps con GitHub.
   - Importar el repositorio desde GitHub.
   - Elegir la conexión con GitHub e iniciar sesion con las credenciales de GitHub.
   - Seleccionar el repositorio que deseas importar o conectar con Azure DevOps.

  1.3 Configurar el pipeline en Azure DevOps.
   - Ir a la seccion de "pipelines" y seleccionar "Crear pipeline".
   - Seleccionar "GitHub" como la fuente del código.
   - Elige tu repositorio de GitHub.

  1.4 Configurar los servicios de Azure.
   - Crear un Registro de Contenedores de Azure, Azure Container Registry (ACR).
   - En el portal de Azure, crea un Registro de Contenedores de Azure (ACR).
   - Crear un clúster de AKS.
   - En el portal de Azure, crea un clúster de AKS.
   - Conectar Azure Container Registry con AKS.

   1.5 con el siguiente comando en la CLI de Azure para permitir que AKS extraiga imágenes de tu ACR.

    - az aks update -n "tu-cluster" -g "tu-resource-group" --attach-acr "tu-registry"

   1.6 Configurar el service principal.
   - Crea un servicio principal en Azure

    - az ad sp create-for-rbac --name "<nombre del sp>" --role contributor --scopes /subscriptions/<tu-subscription-id> --sdk-auth
   - Guarda el resultado JSON, que contiene las credenciales necesarias.

   1.7 Agregar Variables en Azure DevOps:

   - Ve a la sección "Pipelines" en Azure DevOps y selecciona "Library".
   - Crea un nuevo grupo de variables e ingresa las credenciales del servicio principal.
   
   1.8 Ejecutar el Pipeline

  - Commit y Push del Archivo YAML:
  - Realiza un commit y push del archivo azure_pipelines_k8s.yml a tu repositorio de GitHub.
  
  1.9 Ejecutar el Pipeline:
  - En Azure DevOps, ve a "Pipelines" y selecciona tu pipeline recién creado.
  - Haz clic en "Run pipeline" para iniciar el proceso de despliegue.

## Resumen

Basicamente en esta readme se explica la respectiva configuración que se solicita en los entregables, antes que nada quiero agradecer por tener en cuanta mi perfil, gracias por la oportunidad de poder ser participe de este reto.

Saludos, 

Santiago Morales.

+57 3225302285
