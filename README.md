# medico-
from datetime import date

class Entidad:
    def Agregar(self):
        print(f"{self.__class__.__name__} agregado correctamente")
    
    def Modificar(self):
        print(f"{self.__class__.__name__} modificado correctamente")
    
    def Eliminar(self):
        print(f"{self.__class__.__name__} eliminado correctamente")
        
    def ListaDeConsulta(self):
        print(f"Listado: \n{self.__class__.__name__}")

class Paciente(Entidad):
    def __init__(self, id: str, nombre: str, edad: int, genero: str, email: str, telefono: str, direccion: str):
        self.id = id
        self.nombre = nombre
        self.edad = edad
        self.genero = genero
        self.email = email
        self.telefono = telefono
        self.direccion = direccion
    
    def ListaDeConsulta(self):
        print(f"Paciente: {self.nombre}, Edad: {self.edad}, Género: {self.genero}")

class Quimico(Entidad):
    def __init__(self, id: str, nombre: str, direccion: str, email: str, telefono: str):
        self.id = id
        self.nombre = nombre
        self.direccion = direccion
        self.email = email
        self.telefono = telefono
    
    def EntregaMedicamentos(self):
        print(f"{self.nombre} ha entregado los medicamentos.")
    
class Laboratorio(Entidad):
    def __init__(self, id: str, nombre: str, direccion: str, email: str, telefono: str):
        self.id = id
        self.nombre = nombre
        self.direccion = direccion
        self.email = email
        self.telefono = telefono
    
    def RecolectarPrueba(self):
        print(f"{self.nombre} ha recolectado la prueba.")
    
    def GenerarInformeLaboral(self):
        print(f"{self.nombre} ha generado el informe laboral.")

class Descripcion(Entidad):
    def __init__(self, idPrescripcion: int, diagnostico: str, nombreMedicina: str, potenciaMedicamento: int, 
                 frecuenciaMedicamento: int, observaciones: str, pruebaLaboratorio: str, 
                 laboratorioInstrucciones: str, preincripcionesEntregar: str, solicitudesLaboratorioRealizadas: str, 
                 montoFactura: float):
        self.idPrescripcion = idPrescripcion
        self.diagnostico = diagnostico
        self.nombreMedicina = nombreMedicina
        self.potenciaMedicamento = potenciaMedicamento
        self.frecuenciaMedicamento = frecuenciaMedicamento
        self.observaciones = observaciones
        self.pruebaLaboratorio = pruebaLaboratorio
        self.laboratorioInstrucciones = laboratorioInstrucciones
        self.preincripcionesEntregar = preincripcionesEntregar
        self.solicitudesLaboratorioRealizadas = solicitudesLaboratorioRealizadas
        self.montoFactura = montoFactura
        
    def GenerarFactura(self):
        print(f"Factura generada con un monto de {self.montoFactura}.")

class Doctores(Entidad):
    def __init__(self, id: str, nombre: str, edad: int, genero: str, calificacion: str, experiencia: str, numeroRegistro: str):
        self.id = id
        self.nombre = nombre
        self.edad = edad
        self.genero = genero
        self.calificacion = calificacion
        self.experiencia = experiencia
        self.numeroRegistro = numeroRegistro
    
    def ListaDeConsulta(self):
        print(f"Doctor: {self.nombre}, Calificación: {self.calificacion}, Experiencia: {self.experiencia}")

class Consultas(Entidad):
    def __init__(self, paciente: Paciente, doctor: Doctores, en_linea_o_cita: str, fecha_solicitud: date, 
                 cadena_sintomas: str, estado_solicitud: str):
        self.paciente = paciente
        self.doctor = doctor
        self.en_linea_o_cita = en_linea_o_cita
        self.fecha_solicitud = fecha_solicitud
        self.cadena_sintomas = cadena_sintomas
        self.estado_solicitud = estado_solicitud
    
    def ListaDeConsulta(self):
        print(f"Consulta de {self.paciente.nombre} con el Dr. {self.doctor.nombre} el {self.fecha_solicitud}")

class Especialista(Doctores, Descripcion, Entidad):
    def __init__(self, ssd: str, nombre: str, descripcion: str):
        self.ssd = ssd
        self.nombre = nombre
        self.descripcion = descripcion

# Ejemplo de uso
paciente1 = Paciente("P001", "Juan Pérez", 35, "Masculino", "juan.perez@email.com", "555-1234", "Calle Falsa 123")
doctor1 = Doctores("D001", "Dr. López", 45, "Masculino", "Excelente", "10 años", "ABC123")
consulta1 = Consultas(paciente1, doctor1, "Cita", date.today(), "Fiebre y dolor de cabeza", "Pendiente")

consulta1.ListaDeConsulta()
