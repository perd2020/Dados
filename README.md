# frecuencia_distribucion_variables_resultados_imitando_juego_de_dados

Frecuencia, Distribución,Resultados y Variables¶
Imitando el juego de dados
![imitando_juego_de_dados - Jupyter Notebook - Google Chrome 22_2_2023 2_16_06 p  m](https://user-images.githubusercontent.com/91780371/220706394-08e74a18-8e28-4431-b0b6-dd7efa96b7a7.png)


#### # Usando la frecuencia relativa, podemos cambiar la escala de la frecuencia para que podamos 
#comparar los resultados de diferentes números de ensayos
![image](https://user-images.githubusercontent.com/91780371/220705545-8cf10b11-59ad-45b6-b859-4cf3c476264c.png)


#### Intentemos aumentar el número de intentos a 10000 y veamos qué sucede...
![image](https://user-images.githubusercontent.com/91780371/220705718-026f5db9-db29-4e68-bf82-e1cd6ecc51db.png)
Podemos ver que con más intentos, el resultado se ve cada vez más estable, y esto es muy parecido a una distribución de probabilidad.
Intente aumentar aún más el número de "pruebas" (pero Jupyter Notebook puede tardar un tiempo en generar el resultado)
![imitando_juego_de_dados - Jupyter Notebook - Google Chrome 22_2_2023 2_15_41 p  m](https://user-images.githubusercontent.com/91780371/220706463-d201b61e-f899-453e-b90a-51314349c309.png)

#### Expectativa y Varianza de una distribución


# supongamos que tenemos dados justos, lo que significa que todas las caras se mostrarán con la misma probabilidad
# entonces podemos decir que conocemos la 'Distribución' de la variable aleatoria - sum_of_dice


X_distri = pd.DataFrame(index=[2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])
X_distri['Prob'] = [1, 2, 3, 4, 5, 6, 5, 4, 3, 2, 1]
X_distri['Prob'] = X_distri['Prob']/36
X_distri


![imitando_juego_de_dados - Jupyter Notebook - Google Chrome 22_2_2023 2_20_20 p  m](https://user-images.githubusercontent.com/91780371/220706360-23de2b03-68a9-4ba4-b606-ca3a8ab73391.png)

#### buscamos la media y la varianza
mean = pd.Series(X_distri.index * X_distri['Prob']).sum()
var = pd.Series(((X_distri.index - mean)**2)*X_distri['Prob']).sum()

mean=6.999999999999998 
var=5.833333333333333


# si calculamos la media y la varianza de los resultados (con un número suficientemente alto de ensayos, por ejemplo, 20000)...

ensayo = 20000
resultado = [die.sample(2, replace=True).sum().loc[0] for i in range(ensayo)]

#imprime la media y la varianza de los 20000 ensayos

resultado = pd.Series(resultado)
print("la media es", resultado.mean(), "la varianza es", resultado.var())

la media es 6.9879 la varianza es 5.849246052304745


